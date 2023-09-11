- Package 
	- `ros2 pkg create myaction_client --build-type ament_python --dependencies rclpy ${MESSAGE_TYPE}` 

```python
#!/usr/bin/env python3 


from myaction_interface.action import MyAction

import rclpy
from rclpy.action import ActionClient
from rclpy.node import Node

from std_msgs.msg import Int16


class myaction_client(Node):
    def __init__(self):
        super().__init__("myaction_client")
        
        self.action_client_ = ActionClient(
            self,
            MyAction,       # action type
            "myAction"      # action name
        )


    def send_goal(self, _msg_desired_number):
        # generate goal
        goal = MyAction.Goal()
        goal.desired_number = _msg_desired_number
        
        # wait for the Action Server to launch
        self.get_logger().info("waiting for server...")
        self.action_client_.wait_for_server()
        
        # send goal
        self.send_goal_ = self.action_client_.send_goal_async(
        goal, 
        feedback_callback= self.callback_feedback
        )
        ## response after sending goal: rejected / accepted
        
		rclpy.spin_until_future_complete(self, self.send_goal_)
		self.goal_handle = self.send_goal_.result()

        if not self.goal_handle.accepted:
            self.get_logger().info("Goal(s) rejected...")
            self.goal_result = goal_result_code.REJECTED
            return

		self.current_number += 1
        self.get_logger().info("Goal(s) accepted...")

		self.get_result()
        
    # callback function for feedback
    def callback_feedback(self, _future):
        # get feedback
        feedback = _future.feedback
        # Message
        msg_current_number = feedback.current_number     # extracting msg from feedback
        # data
        current_number = msg_current_number.data
        
        # output
        self.get_logger().info(
            f"Received Feedback: {current_number}"
        )
	
    def get_result(self):
        self.result_future = self.goal_handle.get_result_async()  
        rclpy.spin_until_future_complete(self, self.result_future)
        
        if self.result_future.result():
            self.get_logger().debug("result available...")
            # get result Status
            self.status = self.result_future.result().status
            # get result
            self.result = self.result_future.result().result
            if self.status == GoalStatus.STATUS_SUCCEEDED:
                self.get_logger().info("result: succeeded...")
            else:
                self.get_logger().info("result: failed...")
        # shutdown
        self.get_logger().info("Service completed, end...")
        rclpy.shutdown()
        

def main(args=None):
    # Initialize the rclpy library
    rclpy.init(args=args)

    # Create the Action Client node
    my_client = myaction_client()

    # Send a goal message
    ## generate message
    msg_goal = Int16()
    msg_goal.data = 5
    ## send
    my_client.send_goal(msg_goal)

    # Spin to execute callbacks
    rclpy.spin(my_client)


if __name__ == '__main__':
    main()
```
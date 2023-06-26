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
        self.send_goal_.add_done_callback(self.callback_goal_response)
        
        
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


    def callback_goal_response(self, _future):
        # Get the goal_handle
        goal_handle = _future.result()
        if goal_handle.accepted == False:
            self.get_logger().info("Goal rejected...")
            return
        
        self.get_logger().info("Goal accepted...")
        # Get the result
        self.get_result_future_ = goal_handle.get_result_async()
        self.get_result_future_.add_done_callback(self.callback_get_result)
  

    def callback_get_result(self, _future):
        # Get the result
        result = _future.result().result
        # Message
        msg_final_number = result.final_number      # extracting msg from result
        # data
        final_number = msg_final_number.data
        
        # output
        self.get_logger().info(
            f"received Result: {final_number}"
        )
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
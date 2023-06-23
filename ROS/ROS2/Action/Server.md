- Package
	- `ros2 pkg create myaction_server --build-type ament_python --dependencies rclpy ${MESSAGE_TYPE}` 

```python
#!/usr/bin/env python3 

import time

from myaction_interface.action import MyAction

import rclpy
from rclpy.action import ActionServer
from rclpy.executors import MultiThreadedExecutor
from rclpy.node import Node

from std_msgs.msg import Int16


class myaction_server(Node):
    def __init__(self):
        # Node name
        super().__init__("myaction_server")
        
        # Action Server
        self.action_server_ = ActionServer(
            self,
            MyAction,               # action type
            "myAction",             # action name
            self.callback_execute   # callback function
        )
        
        # Data definition
        self.current_number = 0
        
    def callback_execute(self, _goal):
        # Request
        request = _goal.request                         # extracting the request from the goal
        # Message
        msg_desired_number = request.desired_number     # extracting msg from request
        # data
        desired_number = msg_desired_number.data        # extracting data from msg
        

        # Process
        self.get_logger().info('Executing goal...')
        while self.current_number < desired_number:
            # Change data
            self.current_number += 1
            # generate message
            msg_current_number = Int16()
            msg_current_number.data = self.current_number
            # generate feedback
            feedback = MyAction.Feedback()
            feedback.current_number = msg_current_number
            # publish feedback
            _goal.publish_feedback(feedback)
            
            time.sleep(1)
            
        _goal.succeed()
        # generate message
        msg_current_number = Int16()
        msg_current_number.data = self.current_number
        # generate Result
        result = MyAction.Result()
        result.final_number = msg_current_number
        
        return result
    
def main(args = None):
    rclpy.init(args=args)
    
    try:
        my_server = myaction_server()
        
        executor = MultiThreadedExecutor(num_threads= 4)
        executor.add_node(my_server)
        
        try:
            executor.spin()
        finally:
            executor.shutdown()
            my_server.destroy_node()
            
    finally:
        rclpy.shutdown()

if __name__ == '__main__':
    main()
```
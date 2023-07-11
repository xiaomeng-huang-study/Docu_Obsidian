- mit Python 
	```bash
	cd ~/ros2_ws/src
	ros2 pkg create my_robot_controller \ 
	--build-type ament_python \ 
	--dependencies rclpy 
	```
- mit C++
	```bash
	cd ~/ros2_ws/src
	ros2 pkg create my_robot_controller \ 
	--build-type ament_cmake \ 
	--dependencies rclcpp 
	```

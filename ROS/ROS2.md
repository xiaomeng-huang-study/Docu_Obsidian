```Shell
colcon build --symlink-install
```

- Pakete erzeugen: 
	```Shell
	cd ~/ros2_ws/src
	ros2 pkg create my_robot_controller \ 
	--build-type ament_python ament_cpp \ 
	--dependencies rclpy 
	```
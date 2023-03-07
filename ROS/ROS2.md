```Shell
colcon build --symlink-install
```

- Pakete erzeugen: 
	```Shell
	cd ~/ros2_ws/src
	ros2 pkg create my_robot_controller \ 
	--build-type ament_python \ 
	--dependencies rclpy 
	```

- build 
	```Shell
	cd ~/ros2_ws
	colcon build
	```
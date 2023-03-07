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

- Node 
	```Shell
	cd ~/ros2_ws/src/my_robot_controller/my_robot_controller
	touch my_first_node.py
	```
	```Shell
	chmod +x my_first_node.py
	```

`import rospy` $\Rightarrow$ `import rclpy` 
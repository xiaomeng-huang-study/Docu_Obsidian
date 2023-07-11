- ROS1 
	- ROS-core
		```ROS
		roscore
		```
	- rosrun 
		```ROS
		rosrun (package_name) (nodename)
		```
	- roslaunch (all nodes) 
		```ROS
		roslaunch (...) (...).launch 
		```

- Beispiel 
	- rqt_robot_steering 
		```ROS
		rosrun rqt_robot_steering rqt_robot_steering 
		```
	- turtlesim 
		```ROS
		rosrun turtlesim turtlesim_node
		```
	- wpr_simulation 
		```ROS
		roslaunch wpr_simulation wpb_simple.launch 
		```
	- ultra_node 
		```ROS
		rosrun ssr_pkg ultra_node.py
		```

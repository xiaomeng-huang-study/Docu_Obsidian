- Package
	- `ros2 pkg create myaction_interface --build-type ament_cmake --dependencies rclpy` 
- `XXX.action` : 
	- XXX: erste Buchstabe groß schreiben, z.B. MyAction
	- in `action` Ordner 
	```
	# Request
	---
	# Result
	---
	# Feedback
	```
- in `CMakeLists.txt` : 
	```
	find_package(rosidl_default_generators REQUIRED)
	find_package(${MESSAGE_TYPE} REQUIRED)
	
	rosidl_generate_interfaces(${PROJECT_NAME}
	  "action/XXX.action"
	  DEPENDENCIES ${MESSAGE_TYPE}
	)
	```
- in `package.xml` : 
	```
	<buildtool_depend>rosidl_default_generators</buildtool_depend>
	
	<depend>action_msgs</depend>
	<depend>${MESSAGE_TYPE}</depend>
	
	<member_of_group>rosidl_interface_packages</member_of_group>
	```
- `colcon build` 
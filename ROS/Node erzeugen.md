roscd roscpp 

- node erstellen 
	- ${PACKAGE_NAME}/src/(XXX)\_node.cpp 
		```c++
		#include <ros/ros.h>

		int main(int argc, char* argv[])
		{
			ros::init(argc, argv, "(XXX)_node");
			
			while(ros::ok())
			{
				...
			}
		}
		```
	- ${PACKAGE_NAME}/scripts/(XXX)\_node.py 
		```python
		#!/usr/bin/env python3
		#coding = utf-8
		import rospy
	
		if __name__ == "__main__":
			rospy.init_node("(XXX)_node")
				#rospy.logwarn("Node initialized successfully!")
		
			while not rospy.is_shutdown():
				...
		```

- Kompilieren(nur bei C++) 
	- in CMakeLists.txt 
		```ROS
		###########
		## Build ##
		###########
		
		## Declare a C++ executable
		## With catkin_make all packages are built within a single CMake context
		## The recommended prefix ensures that target names across packages don't collide
		# add_executable(${PROJECT_NAME}_node src/ssr_pkg_node.cpp)
		
		
		## Specify libraries to link a library or executable target against
		# target_link_libraries(${PROJECT_NAME}_node
		#   ${catkin_LIBRARIES}
		# )
		```
	- in Terminal 
		```ROS
		cd ~/catkin_ws
		catkin_make
		```
- Recht bekommen(nur bei Python) 
	```ROS
	cd ~/catkin_ws/src/${PACKAGE_NAME}/scripts/
	chmod +x (XXX)_node.py
	```
	- `chmod` : change mode
	- `x` : execute

- Beispiel 
	- ultra_node 
		- in C++
			- ssr_pkg/src/ultra_node.cpp 
				```c++
				int main(int argc, char* argv[])
				{
					ros::init(argc, argv, "ultra_node");
	
					while(ros::ok())
					{
						...
					}
				}
				```
			- Kompilieren 
				- in CMakeLists.txt 
					```
					add_executable(ultra_node src/ultra_node.cpp)
					
					target_link_libraries(ultra_node
					  ${catkin_LIBRARIES}
					)
					```
				- in Terminal 
					```ROS
					cd ~/catkin_ws
					catkin_make
					```
		- in Python 


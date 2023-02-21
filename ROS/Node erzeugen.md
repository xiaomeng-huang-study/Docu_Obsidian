roscd roscpp 

- node erstellen 
	- ssr_pkg/src/(XXX)\_node.cpp 
		```c++
		#include <ros/ros.h>

		int main(int argc, char* argv[])
		{
			ros::init(argc, argv, "(XXX)_node");
			...
		}
		```
- Kompilieren 
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

- Beispiel 
	- ultra_node 
		- ssr_pkg/src/ultra_node.cpp 
			```c++
			int main(int argc, char* argv[])
			{
				ros::init(argc, argv, "ultra_node");
				...
			}
			```
		- Kompilieren 
			- in CMakeLists.txt 
				```
				add_executable(ultra_node src_pkg/src/ultra_node.cpp)
				
				target_link_libraries(ultra_node
				  ${catkin_LIBRARIES}
				)
				```
			- in Terminal 
				```ROS
				cd ~/catkin_ws
				catkin_make
				```

- dauerhaft in Betrieb 
	```c++
	while(ros::ok())
	{
	...
	}
	```
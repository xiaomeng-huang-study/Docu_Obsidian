- e.g. `cv_bridge in OpenCV
	```cmake
	# Find necessary ROS packages
	find_package(catkin REQUIRED COMPONENTS
	  roscpp
	  cv_bridge
	)
	
	# Find OpenCV package
	find_package(OpenCV REQUIRED)
	
	# Include directories for OpenCV
	include_directories(${OpenCV_INCLUDE_DIRS})
	
	# Specify your project dependencies
	catkin_package(
	  CATKIN_DEPENDS roscpp cv_bridge
	)
	
	# Add your executable or library
	add_executable(your_executable src/your_source_file.cpp)
	
	# Link your executable to required libraries
	target_link_libraries(your_executable
	  ${catkin_LIBRARIES}
	  ${OpenCV_LIBRARIES}
	)
	
	```
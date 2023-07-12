- Ordner Struktur 
	```
	workspace_folder/        -- WORKSPACE z.B. catkin_ws
	  src/                   -- SOURCE SPACE
	    CMakeLists.txt       -- 'Toplevel' CMake file, provided by catkin
	    package_1/
	      CMakeLists.txt     -- CMakeLists.txt file for package_1
	      package.xml        -- Package manifest for package_1
	    ...
	    package_n/
	      CMakeLists.txt     -- CMakeLists.txt file for package_n
	      package.xml        -- Package manifest for package_n
	```

## von Außen bekommen 
### APT 


- install 
	```ROS
	sudo apt install ros-${ROS-DISTRO}-${PACKAGE_NAME}
	```
	- ROS1 
		- https://index.ros.org/packages/#noetic 
		- Beispiel 
			- rqt_robot_steering 
				- https://index.ros.org/p/rqt_robot_steering/github-ros-visualization-rqt_robot_steering/#noetic 
				- Beschreibung: http://wiki.ros.org/rqt_robot_steering 
				```ROS
				cd ~
				sudo apt install ros-noetic-rqt-robot-steering
				```
			- turtlesim 
				- https://index.ros.org/p/turtlesim/github-ros-ros_tutorials/#noetic 
				- Beschreibung: https://wiki.ros.org/turtlesim 
				```ROS
				cd ~
				sudo apt install ros-noetic-turtlesim
				```
	- ROS2 
		- https://index.ros.org/packages/#foxy 


### GitHub 
- git clone 
	- (Falls git nicht installiert) 
		- `sudo apt install git` 
	```ROS
	cd ~/ros_ws/src/
	git clone ...
	```
	- ROS1 
		- Kompilieren 
			```bash
			cd ~/ros1_ws
			catkin_make
			```
		- development Environment 
			```bash
			source ~/ros1_ws/devel/setup.bash
			```
			- kann in `.bashrc` hinzugefügt werden 
				```bash
				gedit ~/.bashrc
				```
				- am Ende von `.bashrc` 
					```bash
					source ~/ros1_ws/devel/setup.bash
					```
	- ROS2 
		- Kompilieren 
			```bash
			cd ~/ros2_ws
			colcon build --${PARAMETERS}
			```
		- development Environment 
			```bash
			source ~/ros2_ws/install/setup.bash
			```
			- kann in `.bashrc` hinzugefügt werden 
				```bash
				gedit ~/.bashrc
				```
				- am Ende von `.bashrc` 
					```bash
					source ~/ros2_ws/install/setup.bash
					```


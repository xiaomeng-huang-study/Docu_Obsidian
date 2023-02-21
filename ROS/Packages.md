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


## APT
https://index.ros.org/packages/#noetic 

- install 
```ROS
sudo apt install ros-noetic-(package_name)
```

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

## GitHub 
- git clone 
	- Falls git nicht installiert 
		- `sudo apt install git` 
	```ROS
	git clone ...
	```
- install for noetic 
	```ROS
	cd .../scripts
	./install_for_noetic.sh
	```
- Kompilieren 
	```ROS
	cd ~/catkin_ws
	catkin_make
	```
- development Environment 
	```ROS
	source ~/catkin_ws/devel/setup.bash
	```
	- in `.bashrc` hinzugefügen 
		```ROS
		...
		source ~/catkin_ws/devel/setup.bash
		```

- Beispiel 
	- wpr_simulation 
		- github: https://github.com/6-robot/wpr_simulation.git 


- ssr_pkg 
	```ROS
	catkin_create_pkg ssr_pkg rospy roscpp std_msgs
	``` 
	
- Topic_Name klären 
- Message_Typ klären 
	- https://wiki.ros.org/std_msgs 
- Header-Datei includieren 
	- z.B. `String` 
		- http://docs.ros.org/en/api/std_msgs/html/msg/String.html 
		```c++
		include <std_msgs/String.h>
		```
- Message definieren 
	```c++
	std_msgs::$Message_Typ$ msg;
	```
- Nodehandler definieren 
	```c++
	ros::NodeHandle nh;
	```
- Publischer definieren 
	```c++
	ros::Publisher pub = nh.advertise<std_msgs::$Message_Typ$>($Topic_Name$, $Latenz$);
	```
- Data zuweisen 
	```
	msg.data = ...;
	```
- publish 
	```c++
	pub.publish(msg);
	```

- Frequenz einstellen/ Delay einsetzen 
	```c++
	ros::Rate loop_rate(Anzahl_pro_Sekunde);
	```
	- in while-Schleife 
	```c++
	loop_rate.sleep();
	```

- Beispiel 
	```c++
	#include "ros/ros.h"
	#include <std_msgs/String.h>
	
	int main(int argc, char *argv[])
	{
	    ros::init(argc, argv, "ultra_node");
	    ros::NodeHandle nh;
	    ros::Publisher pub = nh.advertise<std_msgs::String>("testTopic", 10);
	
	    std_msgs::String msg;
	    msg.data = "testMessage";
	    ros::Rate loop_rate(10);
	    while(ros::ok())
	    {
	        pub.publish(msg);
	        loop_rate.sleep();
	    }
	    return 0;
	}
	```


- Befehle mit Topic 
	- `rostopic list` 
	- rostopic echo /(Topic_name)
	- rostopic hz /(Topic_name)
- Topic_Name klären 
- Message_Typ klären 
	- https://wiki.ros.org/std_msgs 
- Header-Datei includieren 
	- z.B. `String` 
		- http://docs.ros.org/en/api/std_msgs/html/msg/String.html 
		```c++
		include <std_msgs/String.h>
		```
- Nodehandler definieren 
	```c++
	ros::NodeHandle nh;
	```

## Publischer 
- Publischer definieren 
	```c++
	ros::Publisher pub;
	pub = nh.advertise<std_msgs::${MESSAGE_TYP}>(${TOPIC_NAME}, ${LATENZ});
	```
- Message
	```c++
	std_msgs::${MESSAGE_TYP} msg;
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
	    ros::init(argc, argv, "pub_node");
	    ros::NodeHandle nh;
	    ros::Publisher pub; 
	    pub = nh.advertise<std_msgs::String>("testTopic", 10);
	
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

## Subscriber 
- callback Funktion definieren 
	```c++
	void ${CALLBAKC_FUNCTION_NAME} (std_msgs::${MESSAGE_TYP} msg)
	{
		...
	}
	```
- subscriber definieren 
	```c++
	ros::Subscriber sub; 
	sub = nh.subscribe("testTopic",10,${CALLBACK_FUNCTION_NAME});
	```
- spinOnce
	```c++
	while(ros::ok())
	{
		ros::spinOnce();
		...
	}
	```


- Beispiel 
	```c++
	#include "ros/ros.h"
	#include <std_msgs/String.h>
	
	void pub_callback(std_msgs::String msg)
	{
		printf((msg.data).c_str());
		printf("\n");
			//ROS_INFO((msg.data).c_str());  //mit Zeitstampel
	}
	
	int main(int argc, char* argv[])
	{
		ros::init(argc, argv, "sub_node");
	
		ros::NodeHandle nh;
		ros::Subscriber sub;
		sub = nh.subscribe("testTopic", 10, pub_callback);
	
		while(ros::ok())
		{
			ros::spinOnce();
			...
		}
	}
	```

- Befehle mit Topic 
	- `rostopic list` 
	- `rostopic echo /(Topic_name)` 
	- `rostopic hz /(Topic_name)` 
- ROS-Befehle 
	- `rqt_graph`
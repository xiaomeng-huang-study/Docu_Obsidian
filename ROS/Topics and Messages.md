- Topic_Name klären 
- Message_Typ klären 
	- https://wiki.ros.org/std_msgs 
- Header-Datei 
	- z.B. `String` 
		- http://docs.ros.org/en/api/std_msgs/html/msg/String.html 
		```c++
		include <std_msgs/String.h>
		```
		
		```python
		from std_msgs.msg import String
		```
- Nodehandler definieren 
	```c++
	ros::NodeHandle nh;
	```

## Publisher 
- Publischer definieren 
	```c++
	ros::Publisher pub;
	pub = nh.advertise<${HEADER_MESSAGE_TYP}::${MESSAGE_TYP}>("${TOPIC_NAME}", ${QUEUE_SIZE});
	```

	```python
	pub = rospy.Publisher("${TOPIC_NAME}", ${MESSAGE_TYP}, queue_size = ${QUEUE_SIZE})
	```

- Message definieren 
	```c++
	${HEADER_MESSAGE_TYP}::${MESSAGE_TYP} msg;
	```
	
	```python
	msg = String()
	```

- publish 
	```c++
	msg.data = ...;
	pub.publish(msg);
	```
	
	```python
	msg.data = ...
	pub.publish(msg)
	```

- Frequenz einstellen/ Delay einsetzen 
	```c++
	ros::Rate loop_rate(Anzahl_pro_Sekunde);
	```
	
	```python
	rate = rospy.Rate(Anzahl_pro_Sekunde)
	```

	- in while-Schleife 
	```c++
	loop_rate.sleep();
	```
	
	```python
	rate.sleep()
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
	    pub = nh.advertise<std_msgs::String>("myTopic", 10);
		
	    std_msgs::String msg;
	    msg.data = "myMessage";
	    
	    ros::Rate loop_rate(10);
	    while(ros::ok())
	    {
	        pub.publish(msg);
	        loop_rate.sleep();
	    }
	    return 0;
	}
	```
```python
import rospy
from std_msgs.msg import String

if __name__ == "__main__":
	rospy.init_node("pub_node")
		#rospy.logwarn("Node initialized successfully!")
	pub = rospy.Publisher("myTopic", String, queue_size = 10)
	rate = rospy.Rate(10)
	
	msg = String()
	
	while not rospy.is_shutdown():
		msg.data = ...
		pub.publish(msg)
		rate.sleep()
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
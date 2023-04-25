```c++
#include <ros/ros.h>
#include <std_msgs/String.h>

int main(int argc, char* argv[])
{
    //node initialisieren
    ros::init(argc, argv, "pub_cpp_node");

    //NodeHandle 
    ros::NodeHandle nh;

    //Publischer
    ros::Publisher pub;
    pub = nh.advertise<std_msgs::String>("myTopic",10);

    //Message
    std_msgs::String msg;

    //Frequenz
    ros::Rate loop_rate(10);

    while(ros::ok())
    {
        msg.data = "I am a Message!";
        pub.publish(msg);
        loop_rate.sleep();
    }
    
    return 0;
}
```
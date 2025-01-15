```c++
#include <ros/ros.h>
#include <std_msgs/String.h>

void callback_func(std_msgs::String _msg)
{
    char msg[(_msg.data).length()+1];
    strcpy(msg, (_msg.data).c_str());
    printf("%s\n",msg);
}

int main(int argc, char* argv[])
{
    //node initialisieren
    ros::init(argc, argv, "sub_cpp_node");

    //NodeHandle 
    ros::NodeHandle nh;

    //Subscriber
    ros::Subscriber sub;
    sub = nh.subscribe("myTopic", 10, callback_func);

    while(ros::ok())
    {
        ros::spinOnce();
    }

    return 0;
}
```
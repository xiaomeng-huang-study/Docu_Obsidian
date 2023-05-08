```python
#!/usr/bin/env python3
import rospy
from std_msgs.msg import String

def callback_func (_msg):
    rospy.loginfo(_msg.data)



if __name__ == "__main__":
    rospy.init_node("sub_py_node")

    sub = rospy.Subscriber("myTopic", String, callback_func, queue_size = 10)

    while not rospy.is_shutdown():
        rospy.spin()
```
```python
#!/usr/bin/env python3
import rospy
from std_msgs.msg import String

if __name__ == "__main__":
    rospy.init_node("pub_py_node")

    pub = rospy.Publisher("myTopic", String, queue_size = 10)

    msg = String()

    rate = rospy.Rate(10)

    while not rospy.is_shutdown():
        msg.data = "I am a Message!"
        pub.publish(msg)
        rate.sleep()
```
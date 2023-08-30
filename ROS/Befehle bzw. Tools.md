## ROS
- rqt_graph 
```bash
rqt_graph
```
- rqt_gui 
```bash
ros2 run rqt_gui rqt_gui
```
- view_frames 
```bash
ros2 run tf2_tools view_frames.py 
```
- Rviz2
```bash
ros2 run Rviz2 Rviz2
```
- topic pub
```bash
ros2 topic pub --once /pilot/setpoint ackermann_msgs/msg/AckermannDrive "{speed: 3}"
```
```bash
ros2 topic pub --once /goal_pose geometry_msgs/msg/PoseStamped "{header: {stamp: {sec: 0, nanosec: 0}, frame_id: 'map'}, pose: {position: {x: -200, y: -30, z: 0.0}, orientation: {x: 0.0, y: 0.0, z: 0.3, w: 1.0}}}"
```

## Linux 
- chmod 777
	- makes every single file on the system under / (root) have rwxrwxrwx permissions 
- 
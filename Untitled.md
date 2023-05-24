```bash
ros2 topic pub --once /pilot/setpoint ackermann_msgs/msg/AckermannDrive "{speed: 3}"
```

```bash
ros2 topic pub --once /goal_pose geometry_msgs/msg/PoseStamped "{header: {stamp: {sec: 0, nanosec: 0}, frame_id: 'map'}, pose: {position: {x: -200, y: -30, z: 0.0}, orientation: {x: 0.0, y: 0.0, z: 0.3, w: 1.0}}}"
```
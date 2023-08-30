```python
speed = float(_cmd_vel_msg.linear.x)

steering_angle = float(rotation_to_steeringangle(_cmd_vel_msg.linear.x, _cmd_vel_msg.angular.z, wheelbase))
```

```python
steering_angle = - float(_cmd_vel_msg.angular.z)/math.pi * float(180.0)

steering_angle = - float(_cmd_vel_msg.angular.z)

steering_angle = float(rotation_to_steeringangle(_cmd_vel_msg.linear.x, _cmd_vel_msg.angular.z, wheelbase))

steering_angle = (rotation_to_steeringangle(_cmd_vel_msg.linear.x, _cmd_vel_msg.angular.z, wheelbase))/math.pi * float(180.0)
```
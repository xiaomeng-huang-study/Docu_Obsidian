```python
def callback_get_result(self, _future):
	# get the result_status
	status =  _future.result().status
	# get the result
	result = _future.result().result
	# Message
	msg_missed_waypoints = result.missed_waypoints
	# Data 
	missed_waypoints_index = []
	for msg_missed_waypoint in msg_missed_waypoints:
		missed_waypoints_index.append(msg_missed_waypoint.index)
		
	# output
	self.get_logger().info("missed waypoints:")
	for missed_waypoint_index in missed_waypoints_index:
		self.get_logger().info(
			f"{str(missed_waypoint_index)} "
		)
	
	# shutdown
	if status == nav_result_code.SUCCEEDED:
		self.get_logger().info("Service completed, end...")
		self.result_status = nav_result_code.SUCCEEDED
	else:
		self.result_status = nav_result_code.FAILED
	# rclpy.shutdown()
```

```python
def callback_goal_response(self, _future):
	# get the goal handle
	goal_handle = _future.result()
	if goal_handle.accepted == False:
		self.get_logger().info(f"Goal {str(self.current_waypoint+1)}/ {str(len(self.goal_poses))} rejected...")
		self.goal_result = goal_result_code.REJECTED
		return
	
	self.current_waypoint += 1
	self.get_logger().info(f"Goal {str(self.current_waypoint)}/ {str(len(self.goal_poses))} accepted...")
	self.goal_result = goal_result_code.ACCEPTED
	# get the result
	self.get_result_future_ = goal_handle.get_result_async()
	self.get_result_future_.add_done_callback(self.callback_get_result)
```

```python
def transformPoint(self, _point, _transform):
	# inverse transform
	transform = TransformStamped()
	transform.header.stamp = _transform.header.stamp 
	transform.header.frame_id = _transform.child_frame_id
	transform.child_frame_id = _transform.header.frame_id
	transform.transform = _transform.transform
	
	pointIn = PointStamped()
	pointIn.header.frame_id = _transform.child_frame_id
	pointIn.point.x = _point.point.x
	pointIn.point.y = _point.point.y
	pointIn.point.z = _point.point.z
	
	
	try:
		PointOut = tf2_geometry_msgs.do_transform_point(pointIn, transform)
		return PointOut
	except: 
		self.get_logger().error(
			f"Could not transform the point from {transform.header.frame_id} to {transform.child_frame_id}"
		)
		return None
```

```python
class State_sendGoal(State):
    # global nav_Robot
    def __init__(self):
        super().__init__(["accepted", "rejected"])


    def execute(self, blackboard):
        print("Executing state send Goal")
        
        nav_Robot.send_goal()
        
        # waiting for result of goal: accepted or rejected
        while True:
            if nav_Robot.goal_result != goal_result_code.UNKNOWN:
                break
        
        if nav_Robot.goal_result == goal_result_code.ACCEPTED:
            return "accepted"
        elif nav_Robot.goal_result == goal_result_code.REJECTED:
            return "rejected"

class State_getResult(State):
    # global nav_Robot
    def __init__(self):
        super().__init__(["SUCCEEDED", "FAILED"])
        
    
    def execute(self, blackboard):
        print("Executing state get Result")
        
        while True:
            if nav_Robot.nav_result != nav_result_code.UNKNOWN:
                break
        
        if nav_Robot.nav_result == nav_result_code.SUCCEEDED:
            return "SUCCEEDED"
        else:
            return "FAILED"
```

```python
## calculate Orientation at waypoint
class State_calcOri(State):
    def __init__(self):
        super().__init__(["Ori_calculated"])  
        
    def execute(self, blackboard):
        logging.debug("Executing state calculating Orientation...")
        
        nav_Robot.calcOri()
        
        logging.debug("Exit state calculate Orientation...")
        
        return "Ori_calculated"
```
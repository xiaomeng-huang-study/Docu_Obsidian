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

```python
try:
	# check Obstacle Status
	num_obs = int(0)
	for obj in _objects.objects:
		if self.isObstacle(obj):
			num_obs += 1
	if num_obs == 0:
		# no Obstacle found
		self.flag_obstacle_found = False
		self.flag_obstacle_error = False
		# self.get_logger().warning(
		#     "No Objects found..."
		# )
	elif num_obs == 1:
		# amount of obstacles: 1
		self.flag_obstacle_found = True
		self.flag_obstacle_error = False
	elif num_obs >= 2:
		# # amount of obstacles >= 2
		# self.get_logger().error(
		#     f"{num_obs} Obstacles, this situation cannot be dealt"
		# )
		self.flag_obstacle_found = True
		self.flag_obstacle_error = True
	else:
		# self.get_logger().error(
		#     "Obstacle detection ERROR"
		# )
		self.flag_obstacle_found = False
		self.flag_obstacle_error = True
		
	# Situation with 1 Obstacle
	if self.flag_obstacle_found == True and self.flag_obstacle_error == False:  
		for obj in _objects.objects:
			if self.isObstacle(obj):
				self.get_logger().debug(f"object {_objects.objects.index(obj) + 1} / {len(_objects.objects)} as obstacle found:")
				# get the min_x and max_y
				self.min_x = self.get_min_x(obj) - self.distance_offset
				self.max_y = self.get_max_y(obj)
				# flag converted to True
				self.flag_obstacle_data_available = True
				self.get_logger().debug(
					f"min_x: {self.min_x}, max_y: {self.max_y}"
				)

except:
	# self.get_logger().error(
	#     "Obstacle detection ERROR"
	# )
	self.flag_obstacle_found = False
	self.flag_obstacle_error = True
```

```python
## function to get the minimum on x-axis
def get_min_x(self, _object):
	min_x = float(1000.0)
	for p in _object.shape[0].polygon.points:
		if p.x < min_x:
			min_x = p.x
	return min_x
## function to get the maximum on y-axis
def get_max_y(self, _object):
	max_y = float(-1000.0)
	for p in _object.shape[0].polygon.points:
		if p.y > max_y:
			max_y = p.y
	return max_y
```

```python
try:
	self.angle_final_goal = self.calcAngle_to_final_goal()
	self.angle_point_max_y = self.calcAngle_to_edge_point_max_y(_obj)
	self.angle_point_min_y = self.calcAngle_to_edge_point_min_y(_obj)
	if self.angle_point_max_y < self.angle_point_min_y:
		self.get_logger().error(
			f"Angle of point with max_y({self.angle_point_max_y}) is bigger than that of point with min_y({self.angle_point_min_y})!!!"
		)
		self.flag_obstacle_error = True
		return
	
	# distance
	distance = math.sqrt(self.final_goal_baselink.pose.position.x ** 2 + self.final_goal_baselink.pose.position.y ** 2)
	if self.angle_final_goal >= self.angle_point_max_y:
		# Situation 1
		self.get_logger().info("Situation 1")
		self.flag_Situation_1 = True
		self.flag_Situation_2 = False
		self.flag_Situation_3 = False
		# angle
		angle_diff = self.angle_final_goal - self.angle_point_max_y
		if self.checkSpaceremaining(distance, angle_diff):
			return True
		else:
			return False
	elif self.angle_point_max_y > self.angle_final_goal >= self.angle_point_min_y:
		# Situation 2
		self.get_logger().info("Situation 2")
		self.flag_Situation_2 = True
		self.flag_Situation_1 = False
		self.flag_Situation_3 = False
		return False
	elif self.angle_final_goal <= self.angle_point_min_y:
		# Situation 3
		self.get_logger().info("Situation 3")
		self.flag_Situation_3 = True
		self.flag_Situation_1 = False
		self.flag_Situation_2 = False
		# angle
		angle_diff = self.angle_point_min_y - self.angle_final_goal
		if self.checkPassability(distance, angle_diff):
			return True
		else:
			return False
	else:
		self.get_logger().error(
			"Cannot check Passability"
		)
		self.flag_obstacle_error = True
		return 
except:
	self.get_logger().error(
		f"Cannot get angles to final goal, edge point with min_y, edge point with max_y"
	)
```

```python
### Check the remaining space
#### compared with the avoidance_radius
def checkSpaceremaining(self, _distance, _angle):
	space_remaining = _distance * math.sin(abs(_angle))
	if space_remaining > self.avoidance_radius:
		return True
	else:
		return False

### Calculate the Angle of final goal in frame baselink
def calcAngle_to_final_goal(self):
	try:
		x = self.final_goal_baselink.pose.position.x
		y = self.final_goal_baselink.pose.position.y
		if x < float(0):
			angle = math.pi + math.atan(y / x)
		else:
			angle= math.atan(y / x)
	except:
		self.get_logger().error(
			f"Cannot calculate the angle to final goal"
		)
		return None
	
	return angle

### Calculate the Angle of edge point with max_y in frame baselink
def calcAngle_to_edge_point_max_y(self, _object):
	# get the edge point with min_y
	max_y = float(-1000.0)
	index_with_max_y = -1
	for p in _object.shape[0].polygon.points:
		if p.y > max_y:
			self.max_y = p.y
			index_with_max_y = _object.shape[0].polygon.points.index(p)
	
	# calculate Angle to the point
	try:
		x = _object.shape[0].polygon.points[index_with_max_y].x
		y = _object.shape[0].polygon.points[index_with_max_y].y 
		if x < float(0):
			angle = math.pi + math.atan(y / x)
		else:
			angle = math.atan(y / x)         
	except:
		self.get_logger().error(
			f"Cannot calculate the angle to edge point with max_y"
		)
	
	return angle

### Calculate the Angle of edge point with min_y in frame baselink
def calcAngle_to_edge_point_min_y(self, _object):
	# get the edge point with min_y
	min_y = float(1000.0)
	index_with_min_y = -1
	for p in _object.shape[0].polygon.points:
		if p.y < min_y:
			self.min_y = p.y
			index_with_min_y = _object.shape[0].polygon.points.index(p)
	
	# calculate Angle to the point
	try:
		x = _object.shape[0].polygon.points[index_with_min_y].x
		y = _object.shape[0].polygon.points[index_with_min_y].y 
		if x < float(0):
			angle = math.pi + math.atan(y / x)
		else:
			angle = math.atan(y / x)
	except:
		self.get_logger().error(
			f"Cannot calculate the angle to edge point with min_y"
		)
	
	return angle
```

```python
## Transform Pose
def transformPose(self):
	if self.flag_tf_available == True:
		# transform available
		transform = self.getTransform()
		# inverse transform
		transform_inv = TransformStamped()
		transform_inv.header.stamp = transform.header.stamp 
		transform_inv.header.frame_id = transform.child_frame_id
		transform_inv.child_frame_id = transform.header.frame_id
		transform_inv.transform = self.inverseTransform(transform.transform)

		# 1.Method
		try:
			PoseOUT = tf2_geometry_msgs.do_transform_pose_stamped(self.goal, transform_inv)
			return PoseOUT
		
		# 2.Method
		# try:
		#     PoseOUT = self.tf_buffer.transform(self.goal, Frames.Frame_ODOM)
		#     return PoseOUT

		except: 
			self.get_logger().error(
				"Could not transform the pose!!!"
			)
			return None
	else:
		self.get_logger().error(
			"Transform not available..."
		)
		return None
```

```python
# waiting for nav_result
while True:
	nav_Robot.get_result()
	if nav_Robot.nav_result != nav_result_code.UNKNOWN:
		break
```

```python
# waiting for goal_result: accepted or rejected?
while True:
	if nav_Robot.goal_result != goal_result_code.UNKNOWN:
		break
```

```python
# if the request to get the result has not been sent, send the request
if self.flag_request_get_result_sent == False:
	self.result_future = self.goal_handle.get_result_async()
	
	rclpy.spin_until_future_complete(self, self.result_future)
	
	self.flag_request_get_result_sent = True
```

```python
try:
	final_goal_odom = self.transformPose(self.final_goal, Frames.Frame_ODOM, Frames.Frame_WORLD)
	try:
		self.final_goal_baselink = self.transformPose(final_goal_odom, Frames.Frame_BASELINK, Frames.Frame_ODOM)
		self.flag_final_goal_is_normal = True
		
		# compare the distance
		distance_to_final_goal = math.sqrt(self.final_goal_baselink.pose.position.x ** 2 + self.final_goal_baselink.pose.position.y ** 2)
		self.get_logger().debug(
			f"Distance to final goal: {distance_to_final_goal}m"
		)
		if distance_to_final_goal <= float(1.5):
			self.flag_nav_completed = True
		else:
			self.flag_nav_completed = False
	except:
		f"Cannot get the transformed pose of goal in frame {Frames.Frame_BASELINK}"
		self.flag_final_goal_is_normal = False
except:
	self.get_logger().error(
		f"Cannot get the transformed pose of goal in frame {Frames.Frame_ODOM}"
	)
	self.flag_final_goal_is_normal = False
```

```python
# generate Goal Message
def generateGoalMsg(self):
	goal_poses = []
	
	try:
		goal_pose_1 = self.transformPose(self.goal, Frames.Frame_WORLD, Frames.Frame_BASELINK)
		
		goal_poses.append(goal_pose_1)
		
		# goal_pose_2 = ...
		# goal_poses.append(goal_pose_2)
		
		self.goal_poses = goal_poses
	except:
		self.get_logger().error(
			"Cannot get the transformed goal_pose_1"
		)
```

```python
## generate Goal Message in Frame_WORLD
class State_generateGoalMsg(State):
    def __init__(self):
        super().__init__(["GoalMsg_generated", "GoalMsg_not_generated"])
        
    def execute(self, blackboard):
        logging.info("Enter state generating Goal Message...")
        
        nav_Robot.generateGoalMsg()
        
        # logging.debug("Exit state generate Goal Message...")
        
        if len(nav_Robot.goal_poses) != 0:
            logging.info("Goal Message was generated")
            return "GoalMsg_generated"
        else:
            logging.error("Goal message not successfully generated!!!")
            return "GoalMsg_not_generated"
```
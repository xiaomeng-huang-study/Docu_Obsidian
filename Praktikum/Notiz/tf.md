- tf: Transform 
	- `map`: globale Darstellung von Entfernung 
	- `odom`: Startposition von Roboter, für lokale konsistente Darstellung von Entfernung 
	- `base_link`: ein Koordinatensystem, das an einer festen Position auf dem Roboter angebracht ist, in der Regel am Hauptchassis und an seinem Rotationszentrum. 
- Map -> odom: AMCL SLAM GPS usw. 
- odom -> base_link : Lidar, Radar, wheel encoders IMUs usw. 
- base_link -> lidar: URDF(Unified Robot Description Format) 
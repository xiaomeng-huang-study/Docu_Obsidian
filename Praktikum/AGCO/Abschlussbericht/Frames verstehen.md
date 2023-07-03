- In der Robotik ist ein "frame" ein Bezugssystem, das verwendet wird, um die Position und Orientierung von Objekten oder Koordinaten im Raum zu beschreiben. 
- Frames werden verwendet, um die Positionen und Orientierungen von Objekten oder Koordinaten im Raum zu beschreiben. Sie bieten eine einheitliche Referenz für die Kommunikation zwischen verschiedenen Komponenten eines Roboters oder Systems. Indem verschiedene Frames miteinander verbunden werden, kann die Beziehung und Positionierung von Objekten im Raum beschrieben werden.

## Frames
- Gängige Frames in ROS bzw. Frames nach dem Standard REP 105, das als eine Voraussetzung für nav2 ist. 
	- (REP 105 vorstellen: REP 105 definiert die Rahmen und Konventionen, die für die Navigation und das größere ROS-Ökosystem erforderlich sind. Diese Konventionen sollten jederzeit befolgt werden, um die umfangreichen Positionierungs-, Odometrie- und Slam-Projekte zu nutzen.) 
	- "map": Das "map"-Frame repräsentiert die globale Karte. Es ist ein festes Bezugssystem, das normalerweise relativ zur Umgebung oder einem festen Punkt definiert ist.
	- "odom": Das "odom"-Frame steht für "odometry" und repräsentiert die geschätzte Position und Orientierung des Roboters basierend auf den zurückgelegten Wegen und den Odometriedaten. Hier wird das zur Startposition vom Traktor festgelegt. 
	- "base_link": Das "baselink"-Frame ist das Basisframe des Roboters. Hier wird das zur Position von Hinterachse des Traktors festgelegt. 
	- "\[sensor frames\]": Das Frame bezieht sich auf ein spezifisches Sensorbezugssystem, das normalerweise mit einem Sensor wie einer Kamera, einem Lidar oder einem IMU (Inertial Measurement Unit) verbunden ist. Es wird verwendet, um die Messungen und Daten des Sensors in einem bestimmten Bezugssystem zu repräsentieren. Hier wird das zur Position des Lidar-Sensors festgelegt. 

## Transformation
- Um eine einheitliche Darstellung der Position und Ausrichtung der Objekte zu ermöglichen, werden die verschiedenen Koordinatensystem miteinander durch die Transformation verknüpft. Dadurch können die Komponenten effektiv miteinander kommunizieren und kooperieren. 
- Die Transformation spielt eine wichtige Rolle bei der Lokalisierung und Navigation von Robotern. Durch die Verfolgung und Aktualisierung der Transformationen zwischen verschiedenen Frames kann der Roboter seine genaue Position in der Umgebung bestimmen und effiziente Navigationspfade planen. 

## Tf
- Das Nachrichtentyp "tfMessage" ist Teil des ROS (Robot Operating System) und wird verwendet, um Transformationsinformationen zwischen verschiedenen Frames zu übertragen. Es ist eine strukturierte Nachricht, die eine Sammlung von Transformationsnachrichten enthält.
- Die Bedeutung liegt darin, die aktuelle Position und Ausrichtung von Objekten oder Frames in einem ROS-System zu übermitteln. 
- Jede Transformation in der `tfMessage` besteht aus zwei Koordinatensystemen: dem Ausgangskoordinatensystem (source frame) und dem Zielkoordinatensystem (target frame). Die Transformation beschreibt die Position und Ausrichtung des Zielkoordinatensystems relativ zum Ausgangskoordinatensystem. Die Translation und Rotation in der Transformation geben an, wie das Zielkoordinatensystem relativ zum Ausgangskoordinatensystem verschoben oder gedreht ist. Dies ermöglicht es ROS-Knoten, die Position und Ausrichtung von Objekten oder Koordinatensystemen zu aktualisieren und die Transformationen zwischen verschiedenen Frames zu verfolgen.
- http://docs.ros.org/en/noetic/api/geometry_msgs/html/msg/TransformStamped.html 


## Tf2
- TF2 ist eine Bibliothek in ROS 2, die verwendet wird, um zeitabhängige Transformationen darzustellen und zu erhalten. 
- TF2 ermöglicht es, die Transformationen zwischen verschiedenen Frames zu verfolgen und zu synchronisieren. Es stellt Funktionen bereit, um die Transformationen zu verwalten, zu aktualisieren und zu erhalten, so dass verschiedene Komponenten eines ROS 2-Systems auf aktuelle und zeitlich abgestimmte Transformationen zugreifen können. 
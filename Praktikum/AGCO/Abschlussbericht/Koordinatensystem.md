- sinnvoll 
- Die Koordinatensystemwandlung wird erforderlich, um sicherzustellen, dass die Position und Ausrichtung von Objekten oder Koordinatensystemen in einem einheitlichen Referenzrahmen interpretiert und verwendet werden können. Dies ermöglicht es, Daten zwischen verschiedenen Systemen auszutauschen und korrekte räumliche Beziehungen herzustellen.
- ROS verwendet ein rechtsorientiertes Koordinatensystem("FLU":forward, left, up), während Unity standardmäßig ein linksorientiertes Koordinatensystem verwendet("RUF": right, up, forward). Durch die Wandlung der Koordinatensysteme kann die Position und Ausrichtung von Objekten in Unity entsprechend der ROS-Konvention interpretiert werden. 
- ![](https://github.com/siemens/ros-sharp/wiki/img/Dev_ROS_Unity_Coordinate_Systems.PNG) 
- Conversion
	- https://github.com/Unity-Technologies/ROS-TCP-Connector/blob/main/ROSGeometry.md 
	- Mit den bereitgestellten Funktionen in der ROS-TCP-Connector-Bibliothek wird die Umsetzung von Koordinatentransformationen und räumlichen Operationen deutlich vereinfacht. 
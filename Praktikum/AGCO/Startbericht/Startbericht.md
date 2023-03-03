Fendt ist ein Unternehmen, das Landtechnik herstellt, insbesondere Traktoren und Erntemaschinen. Landmaschinen intelligent und automatisiert zu machen, ist eine der wichtigsten Aufgaben. 

Zu diesem Thema stelle ich meine Arbeit während meines Praktikums in zeitlicher und inhaltlicher Hinsicht vor. 

## inhaltlich: 
- 1) Integration von vorhandenen ROS-Pakete 
	- Durch Pakete werden die modulare Eigenschaften und Skalierbarkeit des ROS-Systems verbessert. Die hinzufügende, vorhandene Pakete sind  "Swath Detection", "Collision Avoidance", "Path Planner". Sobald die Pakete integriert sind, sollten die mit den anderen Komponenten des ROS-Systems richtig funktionieren. 
- 2) Validierung von den Schnittstellen zwischen ROS und Unity 
	- Die vom ROS gelieferten Richtungs- und Geschwindigkeitsinformationen sollten von Matlab/Simulink korrekt in Positionsinformationen umgewandelt und in Unity simuliert werden. 
	- ROS kann auch die in Unity simulierten Sensoren verwenden, um zu erkennen, was in der Umgebung vor sich geht, und um Entscheidungen zu treffen und Anweisungen für das weitere Vorgehen zu geben. Dies führt zu einem vollständigen Gegenkopplungsmechanismus. 
- 3) Anpassung der Simulationsumgebung 
	- Die Entwicklung einer simulierten Umgebung ist ein wichtiger Schritt bei Inbetriebnahme, um sicherzustellen, dass sie ordnungsgemäß funktioniert und betriebsbereit ist. Die Simulationsumgebung sollte die reale Umgebung so genau wie möglich simulieren und vorwegnehmen, was in der Realität passieren könnte. 
- 4) Erweiterung 
	- Sensor-Modell analysieren 
		- Die Daten des Lasersensors werden analysiert, um festzustellen, ob es notwendig ist, eine Kamera hinzuzufügen, um die Genauigkeit der Objekterkennung zu verbessern. 
	- Matlab/ Simulink Modell analysieren 
		- mit Matlab/ Simulink wird ein
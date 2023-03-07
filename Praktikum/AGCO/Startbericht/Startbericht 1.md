## Hintergrund: 
 AGCO ist ein Unternehmen, das Landtechnik herstellt, insbesondere Traktoren und Erntemaschinen. Landmaschinen intelligent und automatisiert zu machen, ist eine der wichtigsten Aufgaben. 
 
- AGCO ist globale Konzern, Landtechnikbranche 
- Fendt als ein Teil, Prio  
- Premium, Full-line, Landwirtschaft eingesetzt 
	- Traktoren
	- Smart Farming
	- usw. 
- Abteilung 
	- Vorentwicklung 
	- Autonomie, Robotik, Alternativer Antrieb 
		- Schwerpunkt: Autonomie 
			- Simulation + Test Autonomie-Funktionen 
			- 

Zu diesem Thema stelle ich meine Arbeit während meines Praktikums in inhaltlicher und zeitlicher Hinsicht vor. 
- Software: 
	- Die Software basiert hauptsächlich auf dem ROS-System. Mit Unity und Matlab/Simulink können virtuelle Umgebungen für spätere Analysen erstellt werden. 
- Hardware:
	- Ein LIDAR-Sensor wird über der Windschutzscheibe des Traktors installiert, um die Umgebung vor dem Traktor zu scannen. 
	- Auf dem Traktor ist ein Signalturm montiert. Mit einem Fernbedienungsknopf kann es beim Gesundheitsmanagement helfen. 

Simulation 
- Ziel 
	- Mit unity Autonomie-Funktion simuliert 
	- realisiert 
	- Einbinden und Testen 
## inhaltlich: 
- Simulation 
	- 1) Inbetriebnahme 
	- 2) Integration von ROS 
	- 3) Validierung 
	- 4) Erweiterung 
- Versuchstraktor 
	- el. Vorbereitung für Autonomie-Funk. 

- 1) Integration von vorhandenen ROS-Pakete 
	- Durch Pakete für verschiedene Verwendungszwecke werden die modulare Eigenschaften und Skalierbarkeit des ROS-Systems verbessert. 
	- Die hinzufügende, vorhandene Pakete sind  =="Swath Detection", "Collision Avoidance", "Path Planner"==. Sobald die Pakete integriert sind, sollten die mit den anderen Komponenten des ROS-Systems richtig funktionieren. 
		- =="local navigation", "path planner" ==
- 2) Validierung von den Schnittstellen zwischen ROS und Unity 
	- Die vom ROS gelieferten Richtungs- und Geschwindigkeitsinformationen sollten von Matlab/Simulink in Positionsinformationen umgewandelt und korrekt in Unity simuliert werden. 
	- ROS kann auch die in Unity simulierten Sensoren verwenden, um zu erkennen, was in der Umgebung vor sich geht, und um Entscheidungen zu treffen und Anweisungen für das weitere Vorgehen zu geben. Dies führt zu einem vollständigen "closed loop simulation". 
- 3)  der Simulationsumgebung 
	- Die Entwicklung einer simulierten Umgebung ist ein wichtiger Schritt bei Verifikation, um sicherzustellen, dass sie ordnungsgemäß funktioniert und betriebsbereit ist. 
	- Die Simulationsumgebung sollte die reale Umgebung so genau wie möglich simulieren und vorwegnehmen, was in der Realität passieren könnte. 
- 4) Versuchstrator  
	- Für den zuverlässigen und ==sicheren Betrieb== der Maschine sind Funktionen wie "Emergency Stop", die rechtzeitige Signalisierung über Signalturm usw. unerlässlich.
	- Die Hauptaufgabe ist die <font color ="blue">elektrische Verdrahtung</font> und deren Inbetriebnahme bzw. Funktionstest. 
		- Messen 
		- Spannung anlegen 
		- Test auf Traktoren 
	- ==Autonomie-Funktion zu gewährleisten== 
- 5) Erweiterung 
	- Sensor-Modell analysieren 
		- Die Daten des Lasersensors werden analysiert, um festzustellen, ob es notwendig ist, eine Kamera hinzuzufügen, um die Genauigkeit der Objekterkennung zu verbessern. 
	- Matlab/ Simulink Modell analysieren 
		- Mit Hilfe von Matlab/Simulink kann ein dynamisches Modell erstellt werden. Dies ermöglicht eine engere Zusammenarbeit zwischen ROS und Unity 
	- Avoidace-Algorithm erweitern 
		- Der derzeitige Algorithmus befindet sich noch auf einem relativ grundlegenden Niveau. Mit besseren Algorithmen können sich die Traktoren an komplexere Umgebungen anpassen und vernünftigere Entscheidungen treffen. 
- 6) Anwendungsfall 
	- Bodenbearbeitung bzw. Pflügenbearbeitung 
		- Wenn dieses System in der landwirtschaftlichen Produktion eingesetzt werden könnte, würde es die Effizienz erheblich verbessern.

## zeitlich(nur Einschätzung)
- bis Ende März: Gesundheitsverwaltung sollte abgeschlossen sein
- bis Ende Mai: System sollte vervollständigt sein 
- bis Ende September: Anwendungsfall sollte getestet werden 

- grüße euch herzlich zu meinem Vortrag. 
- Ich spreche heute über den Überblick für das Praktikum. 

## Verzeichnis
- Mein Vortrag besteht aus 6 Teilen. 
	- Zuerst würde ich die Sofware und Hardware zeigen. 
	- Anschließend würde ich einen Teil ==vom Startbericht anführen==. Damit haben Sie eine gute ==Verbindung== mit dem Startbericht bzw. ein besseres ==Verständnis== für meine Arbeitspakete. Die Aufgaben werden in essentielle und optionale ==untergeteilt==. In meinem Vortrag würde ich den Fokus auf die essentiellen Aufgaben legen. 
	- Dann würde ich meine Simulationsumgebung zeigen.
		- was sind schon ==vorgegeben== 
	- Im Anschluss würde ich die durchgeführten Aufgaben und die geplanten Aufgaben vorstellen. 
	- Zum Schluss werde ich die grobe Zeitplannung mal sagen. 

## Hintergrund 
- Die hauptsächlich verwendete Software sind ROS-System, Unity und die Verbindung zwischen den beiden. 

- um die ==Entfernungsinformation== aufzunehmen, wird ein Lidar-Sensor auf dem Traktor ==montiert==. Der Sensor richtet sich nach vorne. 
- Und noch ein Traktor für den Test. 

- ROS ist ein flexibles und weit verbreitetes Open-Source-System. 
- Die Eigenschaften P2P und Alle Nachrichten Austausch über Topic sind sehr ==nützlich und hilfreich== für ein autonomes System. 
- Man kann dieses System ==leicht erweitern==. Sinnvoll für ein wachsendes Projekt. 


## Unity 
- mit Unity kann man viel machen. 
- hab 2 Eigenschaften mit Simulation zu tun ==ausgewählt==

- Alle Kommunikation ==finden== durch diesen Server-Endpoint ==statt==. Damit wird eine Verbindung zwischen Unity und ROS erstellt. 


## Arbeitspakete 
- Hier gezeigt werden Arbeitspakete, die ich schon in Startbericht ==aufgelistet== habe. 
- Vielleicht wird es ==übersichtlicher== nach der Sortierung. 
- Meine Hauptaufgaben sind 
	- Unterstürtzung für den Versuchstraktor 
	- ...

## Simulationsumgebung-Unity 
- Wenn ich die Simulation mal ==starte==, dann wird dies Bildschirm angezeigt. 
	- alle Elemente, die mit einem roten Kreis markiert sind, sind UI. Damit kann man eine Feedback von den Informationen bekommen.
		- z.B. ROS info usw. 
## Simulationsumgebung-Interface 
- Dies ist ein großes Projekt. Für mich ist diese Interface wichtig. 
- Hierzu ein Beispiel 
	- Der Traktor ==hört== dem Topic "pilot/setpoint" ==zu==. D.h. Wenn man eine Nachricht zu diesem schickt, um den ==Steuerungsbefehl== zu ==aktualisieren==, wird der Traktor ==aufnehmen== und die ==Bewegung== dazu in Unity zeigen. 
	- Gleichzetig wird der Traktor durch Topic "/simulation_current/ackermann" die aktuelle ==Geschwindigkeit==, den ==Lenkungswinkel== usw. ausgeben.
## Simulationsumgebung-Tf 
- Map -> odom: AMCL SLAM GPS usw. 
- odom -> base_link : Lidar, Radar, wheel encoders IMUs usw. 
- base_link -> lidar: URDF(Unified Robot Description Format) 
## Simulationsumgebungt-Rviz 
- Rviz ist ein sehr gutes ==Visualisierungswerkzeug==. 
- Man kann unterschiedliche Frames darstellen. kann Map eingeben. Man kann auch verschiedene Topics zur Virsualisierung bringen. 

## Integration ROS-Pakete 
- ROS-Pakete für ca von AGCO angeboten. von Lidar-Pionts Aufnahme zu Virsualisierung. 
- das ROS-Paket, das ich ==vervollständigen== muss, ist tractor_ca. Ein wichtiger Topic ist "/col_response". Durch dies Topic kann man die ==Klassifizierung== von der Entfernung für jede Objekt vorne bekommen. 

## Integration ROS-Pakete 
### Nav2-Planner-Controller
- zwei wichtige ==Komponenten== von nav2 sind Planner-Server und Controller-Server. 
	- Planner-Server: für Erstellung von globalen und lokalen Pfaden verantwortlich. 
		- Der globale Planer erzeugt einen Pfad, vom ==aktuellen== Standort zu einem ==Zielort==.
		- Der lokale Planer sorgt dafür, dass der Roboter ==Hindernisse== ausweicht und seine Position in Echtzeit ==korrigiert==. 
	- Controller-Server: für Ausführung der Bewegungen verantwortlich.
		- enthält Algorithmen, die den Roboter steuern und ihn entlang des geplannten Pfades ausführen.
### Nav2-Message-typ
- ==unterschiedliche== Controller können ==unterschiedliche== Message-typ unterstürtzen. 
	- Wenn Steuerungsbefehl auf Typ "Ackermann" eingestellt, wird dies zum Projekt gut passen. Denn ==Sie== haben vielleicht ==gesehen==, in Unity ist Message-Typ auch "Ackermann".
	- Wenn Steuerungsbefehl auf Typ "Twist" eingestellt, wird dies komplizierter.
		- velocity in angular kann Traktor vielleicht ==nicht realisieren==. Denn für Traktoren, ==Drehen auf der Stelle== schwer.
### Nav2-Twist
- Dazu muss diese Message umgesetzt werden. 
	- Ich habe ein ==Algorithmus== dafür geschrieben. Man kann sehen: Velocity in angular in steering_angle umgesetzt. 
### Nav2-Video
- Zum Test habe ich Rviz eine leere Karte eingegeben. 


## Aufgaben in Zukunt-schrittweise 
- Arbeitspakete können schrittweise betracht werden. von Einbauen zu Simulation dann zum Test. 
## Aufgaben in Zukunft-Ziel 
- Traktor kann selbst Pfad plannen, ==Punkte wie orange== einsetzen, dann entlang dem Pfad vom Startpunkt zum Endepunkt fahren. 
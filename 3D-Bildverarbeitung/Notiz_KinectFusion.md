- Bestandteile einer Kamera mit Prime-Sense-Technologie 
	- Infrarot-Laser: Punktemuster (strukturiertes Licht) wird in die zu scannende Umgebung projeziert 
	- Infrarot-CMOS-Sensor: speichert die Bilder 
	- PrimeSense-Chip: berechnet die Tiefeninformation und bestimmt dadurch 3D-Punktewolken bzw. die Tiefenbilder 
- Ein Tiefenwert wird basierend auf der Zeit des Lichtsignals und der Lichtgeschwindigkeit gemessen (time of flight) 
- Nachteile 
	- verrauschte Tiefenbilder: zu vielen Bereichen können keine Daten bestimmt werden 
	- Bereiche ohne Tiefenwerte z.B. bei Materialien, die kein IR-Licht reflektieren bei sehr dünnen Strukturen oder bei Oberflächen, die sich in der Reflektion befinden 
	- zu schneller Bewegung 
- Schritte 
	1. Tiefenkarten aufnehmen:
		- Der Echtzeit-Strom verrauschter Tiefenkarten wird vom Kinect-Sensor erfasst. 
	2. SLAM-Verfahren anwenden:
		- Die Tiefenkarten werden in Echtzeit durch ein hochauflösendes SLAM-Verfahren verarbeitet, um ein inkrementelles 3D-Modell der Szene zu erzeugen. 
	3. Bewegungserkennung durchführen:
		- Die Bewegung des Sensors wird detektiert, und zugehörige Tiefendaten jedes Bildes werden zum Modell hinzugefügt. 
	4. Modell kontinuierlich aktualisieren:
		- Neue Tiefendaten werden durch die Bewegung des Sensors aufgenommen, wodurch das 3D-Modell verfeinert und Lücken geschlossen werden. 
	5. Ansichten fusionieren:
		- Verschiedene Ansichten der physikalischen Szene werden aufgenommen und zu einer einzigen Repräsentation der Szene fusioniert. 
	6. Volumengitter verwenden:
		- Die finale 3D-Repräsentation der Szene basiert auf einem Volumengitter, das die Tiefendaten integriert. 
- GPU Implementierung 
	- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-29_21-14-57.png?raw=" width="80%" /> 
	1. Depth Map Conversion 
		- Die Live-Tiefenbilder werden von Bildkoordinaten in 3DPunkte (Vertices) und Normalen im Kamerakoordinaten-System konvertiert.
	2. Camera Tracking mit ICP 
		- eine rigide 6DOF-Transformation wird mit ICP berechnet, um die aktuellen ausgerichteten Punkte mit dem vorherigen Kamerabild auszurichten. 
	3. Volumetric Integration 
		- eine volumetrische Darstellung für die Oberflächen verwendet. 
		- Durch eine gegebene globale Position der Kamera, können ausgerichtete 3D-Punkte in globale Koordinaten umgerechnet werden und entsprechend im 3D-Voxel-Gitter erneuert werden. Jedes Voxel speichert den laufenden Mittelwert der Abstände zu der angenommenen Position einer physikalischen Oberfläche. 
	4. Raycasting 
		- das Volumen wird mittels einem Raycasting-Algorithmus in Abhängigkeit einer benutzergewählten Kameraansicht gerendert. 
- Wie erreicht KinectFusion die hochauflösende Rekonstruktion der Geometrie? 
	- Voxel-basierte Integration 
	- Parallelisierung durch GPU 
	- Ray-Casting-Rendering 
- Die Auflösung der Geometrie kann auf folgende Weise beeinflusst werden 
	- Voxelgröße 
	- Auflösung der Tiefenbilder 
- Warum ist es wichtig, die Aufnahmen mit der Kinect in einer relativ langsamen Bewegung durchzuführen? 
	- Schnelle Kinect-Bewegung erschwert die Punkt-Alignierung und Camera Tracking beim ICP-Algorithmus. 
- Vorteil der volumetrischen Integration 
	- berücksichtigt Messunsicherheiten
	- nutzt effizient mehrere Messungen,
	- füllt Löcher durch die Hinzunahme neuer Messdaten 
	- gleicht Sensorbewegungen aus 
	- speichert implizit die Oberflächen-Geometrie 
- Wie werden die Daten einer Oberfläche volumetrisch integriert? 
	- signed distance function 
	- Truncated distance function 


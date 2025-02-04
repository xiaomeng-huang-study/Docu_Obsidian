- Bestandteile einer Kamera mit Prime-Sense-Technologie 
	- Infrarot-Laser: Punktemuster (strukturiertes Licht) wird in die zu scannende Umgebung projiziert 
	- Infrarot-CMOS-Sensor: speichert die Bilder 
	- PrimeSense-Chip: berechnet die Tiefeninformation und bestimmt dadurch 3D-Punktewolken bzw. die Tiefenbilder 
- Ein Tiefenwert wird basierend auf der Zeit des Lichtsignals und der Lichtgeschwindigkeit gemessen (time of flight) 
- Nachteile der Asus Xtion Pro Kamera 
	- verrauschte Tiefenbilder: zu vielen Bereichen können keine Daten bestimmt werden 
	- Bereiche ohne Tiefenwerte z.B. bei Materialien, die kein IR-Licht reflektieren bei sehr dünnen Strukturen oder bei Oberflächen, die sich in der Reflektion befinden 
	- zu schneller Bewegung 
- Schritte 
	1. Datenerfassung und Vorbereitung
		- Eingabe:
		    - Tiefenkarte (Depth Map) von einer RGB-D-Kamera.
		    - Intrinsische Kameraparameter (z. B. Brennweite, Bildmittelpunkt).
		- Prozess:
		    - Erfassen der Tiefenwerte jedes Pixels im Bild.
		    - Laden der Kameraparameter, um Tiefenwerte korrekt in 3D-Punkte zu projizieren.
		- Ausgabe:
		    - Roh-Tiefenkarte mit Entfernungswerten pro Pixel.
	2. Depth Map Conversion (Umwandlung in Punktwolken)
		- Eingabe:
		    - Tiefenkarte aus Schritt 1.
		    - Intrinsische Kameramatrix.
		- Prozess:
		    - Jeder Tiefenwert wird mit den intrinsischen Kameraparametern in 3D-Koordinaten (Punktwolke) umgerechnet.
		    - Normalenvektoren werden für jeden Punkt basierend auf benachbarten Punkten berechnet.
		- Ausgabe:
		    - Punktwolke (Vertices) im Kamerakoordinatensystem.
		    - Normalenvektoren für die Punktwolke.
	3. Kamera-Tracking
		- Eingabe:
		    - Punktwolke und Normalenvektoren aus Schritt 2 (aktueller Frame).
		    - Rekonstruiertes Modell aus vorherigen Frames (Volumen oder Punktwolke).
		- Prozess:
		    - Der ICP-Algorithmus berechnet die optimale rigide Transformation (6DOF: Translation und Rotation), um die aktuelle Punktwolke an das Modell auszurichten.
		    - Fehler zwischen korrespondierenden Punkten wird iterativ minimiert.
		- Ausgabe:
		    - 6DOF-Transformation (Kameraposition und -orientierung im globalen Koordinatensystem).
	4. Volumetric Integration (Volumetrische Integration)
		- Eingabe:
		    - Tiefenkarte aus Schritt 1.
		    - Aktuelle Kameraposition (aus Schritt 3).
		    - Voxel-Gitter mit TSDF-Werten (bestehendes globales Modell).
		- Prozess:
		    - Transformiere die Punktwolke aus dem Kamerakoordinatensystem in das globale Koordinatensystem.
		    - Aktualisiere die TSDF-Werte im Voxel-Gitter basierend auf den neuen Tiefenwerten (durch Mittelwertbildung).
		    - Glatte Übergänge entstehen durch das TSDF-Update.
		- Ausgabe:
		    - Aktualisiertes volumetrisches Modell (TSDF-Gitter), das die rekonstruierte Szene repräsentiert.
	5. Raycasting
		- Eingabe:
		    - Aktualisiertes TSDF-Gitter (volumetrisches Modell).
		    - Benutzerdefinierte Kameraansicht oder virtuelle Perspektive.
		- Prozess:
		    - Raycasting-Algorithmus wird angewendet: Strahlen werden durch das Voxel-Gitter geschickt, um Schnittpunkte mit der Oberfläche zu finden.
		    - Sichtbare Oberfläche wird extrahiert und projiziert.
		- Ausgabe:
		    - Tiefenbild oder gerendertes Bild der Oberfläche aus der gewünschten Perspektive.
	6. Iteration und Kontinuierliche Aktualisierung
		- Eingabe:
		    - Nächster Tiefenframe.
		    - Aktuelles TSDF-Gitter.
		- Prozess:
		    - Wiederhole Schritte 2–5:
		        1. Punktwolke berechnen (Schritt 2).
		        2. Kamerabewegung berechnen (Schritt 3).
		        3. Tiefendaten in das Modell integrieren (Schritt 4).
		        4. Oberfläche visualisieren (Schritt 5).
		- Ausgabe:
		    - Kontinuierlich verbessertes volumetrisches Modell der Szene.
- GPU Implementierung 
	- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-29_21-14-57.png?raw=" width="80%" /> 
	1. Depth Map Conversion 
		- Die Live-Tiefenbilder werden von Bildkoordinaten $\rightarrow$ 3D Punkte (Vertices) und Normalen im Kamerakoordinaten-System konvertiert. 
	2. Camera Tracking mit ICP 
		- eine rigide 6DOF-Transformation wird mit ICP berechnet, um die aktuellen ausgerichteten Punkte mit dem vorherigen Kamerabild auszurichten. 
	3. Volumetric Integration 
		- eine volumetrische Darstellung für die Oberflächen verwendet. 
		- Durch eine gegebene globale Position der Kamera, können ausgerichtete 3D-Punkte in globale Koordinaten umgerechnet werden und entsprechend im 3D-Voxel-Gitter erneuert werden. Jedes Voxel speichert den laufenden Mittelwert der Abstände zu der angenommenen Position einer physikalischen Oberfläche. 
	4. Raycasting 
		- das Volumen wird mittels einem Raycasting-Algorithmus in Abhängigkeit einer benutzergewählten Kameraansicht gerendert. 
- Wie erreicht KinectFusion die hochauflösende Rekonstruktion der Geometrie? 
	- Voxel-basierte Integration 
	- Ray-Casting-Rendering 
	- Parallelisierung durch GPU 
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
	- signed distance function: Die Werte sind vor der Oberfläche positiv und hinter der Oberfläche negativ, so dass sich die Oberfläche selbst beim Zero-Crossing bzw. Nulldurchgang zwischen den Voxeln befindet. 
	- Truncated distance function 
- Raycasting 
	- 3D - Volumendaten oder -Modelle auf eine 2D - Bildebene zu projizieren, um eine Visualisierung zu erhalten. 

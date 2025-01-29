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

<img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-29_21-14-57.png?raw=" width="80%" /> 


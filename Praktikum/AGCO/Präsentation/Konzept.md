- Aufforderung vom Professor
	- eine kurze Präsentation der geplanten und durchgeführten Arbeiten (Problemstellung + Umfeld, „Absprungbasis“ (=was ist an Vorarbeiten da/was sind die Voraussetzungen), Detaillierung der Aufgabenstellung und grobe Zeitplanung für die Bearbeitung).

- 1. Seite 
	- Titel: Praktikum bei Fendt: Überlick 
	- Unternehmen: Fendt GmbH
	- Hochschule: Technische Hochschule Ulm
	- Berichter: Xiaomeng, Huang
	- Datum: 09.05.2023
- 2. Seite: Verzeichnis 
	- Hintergrund
		- betroffene Software(S3) und Hardware(S4)
		- Hauptaufgaben 
			- Simulation weiterentwickeln
			- Autonomie-Funktionen durch Testverfahren verbessern
	- einen Teil des Start anführen: besseres Verständnis für Arbeitspakete(S5) 
		- essentielle Aufgabe 
		- optionale Aufgabe 
	- die durchgeführten Aufgaben 
	- die geplanten Aufgaben 



- 3. Seite: Software 
	- ROS
		- Schaubild 
			- ![[ROS.png]] 
		- Vorstellung (optional)
			- bietet eine Vielzahl von Funktionen: Verwaltung von Sensordaten, Steuerung von Robotern. 
			- P2P-System, Knoten-basiertes System: effiziente und flexibele Kommunikation zwischen verschiedenen Modulen.
	- Unity 
		- Schaubild 
			- ![[Unity.jpg]]
		- Vorstellung (optional)
			- umfangreiche Szenarien und Umgebungen erstellen
			- kann realistische physikalische Interaktion simulieren, einschließlich Bewegung, Kollisionen usw. 
	- Verbindung 
		- ROS-Unity-Integration
			- durch Endpoint
		- Bild 
			- ![[ROS-TCP.png]]
- 4. Seite: Hardware 
	- Lidar-Sensor auf dem Traktor 
		- Photo 
	- Traktor für die Testphase 
		- Photo 
- 5. Seite: Arbeitspakete sortieren 
	- Hauptfokus 
		- Versuchstraktor(S6) 
		- Integration vorhandener ROS-Pakete in Simulation(S7) 
			- Pakete von AGCO 
			- Nav2
		- Avoidance-Algorithm erweitern 
		- praktische Prüfung von dem Algorithmen
	- Randbereich 
		- Inbetriebnahme der Simulationsumgebung
		- Validierung von den Schnittstellen zwischen ROS und Unity 
		- Sensor-Modell erweitern 
		- Anpassung der Simulation an den Anwendungsfall 

- 6. Seite: durchgeführte Aufgaben_1 
	- Verdrahtung 
		- Bild: (Kabelsalat) 
		- Methoden 
			- Zangen 
			- löten 
			- usw. 
		- Ziel 
			- praktische Unterstürzung zu Mongoose 
			- praktische Erfahrung mit Elektrotechnik 
- 7. Seite: durchgeführte Aufgaben_2 
	- Importierung von ROS-Paketen "localization" und "navigation"
		- "localization": mithilfe von AMCL-Algorithmus 





- . Seite: ROS-Pakete von AGCO
	- Zone-Erkennung 
		- Schaubild
		- Zone0: noch weit vom Objekt, Zone1: gefährlich, Zone2: sehr nah zum Objekt
- . Seite: nav2
	- nav2 
		- Vorstellung
			- ein Navigationssystem, basiert auf ROS
			- bietet umfangreiche Navigationsalgorithmen und -werkzeugen, erleichtet die Navigation und Pfadplannung
		- Schaubild
			- ![[nav2.png]]
- . Seite: Avoidance-Algorithm erweitern
	- einfache Weise: langsam -> stoppen 
	- komplexe Weise: umgehen 
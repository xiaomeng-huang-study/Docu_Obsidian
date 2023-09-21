<<<<<<< HEAD
=======
# 
>>>>>>> origin/main
- von Firma angeboten 
	- Simulationsumgebung 
		- Traktor-Modell 
		- Feld 
- Ziel 
	- Pfad zum Endpunkt in Echtzeit planen und verfolgen 
	- Hindernis vor dem Traktor-Modell während der Pfadverfolgung vermeiden 
<<<<<<< HEAD

=======
#
>>>>>>> origin/main
- Dazu muss man: 
	- einen Navigation-Stack anwenden  
		- für Pfadplanung und Pfadverfolgung zuständig
	- ein Collision-Avoidance Algorithmus entwickeln
		- für Hindernis-Vermeidung zuständig 
<<<<<<< HEAD


=======
#
>>>>>>> origin/main
- Kontrolle-Modul 
	- nimmt Rückmeldung aus Simulationsumgebung 
	- gibt Bewegungsbefehle aus 
	- --> Damit wird ein geschlossener Kreis gebildet 
<<<<<<< HEAD

=======
#
>>>>>>> origin/main
- Arbeitspakete klar 
	- in 3 Phasen 
		- Vorbereitung 
		- Bearbeitung/ Entwicklung 
		- Integration 
	- Vorbereitung --> Inbetriebnahme 
		- Projektdateien der Simulation holen und die simulierte Umgebung wiederherstellen 
			- Feld 
				- z.B. Boden richtig gezeigt 
			- Traktor 
				- nach den Befehlen (links abb., nach vorne fahren usw.) präzise Bewegungen zeigen 
	- Navigation-Stack 
		- einen geeigneten für autonomes Fahren auswählen 
		- in der Simulation anwenden 
	- Collision-Avoidance Algorithmus 
		- entwickeln 
		- Test dafür 
	- Integration 
		- meine Code in das ganze System integrieren 
		- noch nicht stabil und nicht perfekt --> muss durch andere Ingenieuren korrigiert bzw. verbessert werden 
<<<<<<< HEAD



=======
#
ROS_Vorstellung 
- Modulare Architektur
	- Roboteranwendungen aus wiederverwendbaren und unabhängigen Komponenten aufzubauen. --> "ROS-Package" 
	- Kommunikation über definierte Schnittstellen 
- Kommunikation 
	- als Nächstes mehr erklären 
- Werkzeug und Bibliotheken 
	- Dazu gehören Tools zur Visualisierung, zum Debuggen, zur Simulation und zur Datenanalyse. 
	- Außerdem stehen eine breite Palette von Bibliotheken zur Verfügung, die Funktionen wie Pfadplanung, Lokalisierung, Bildverarbeitung und vieles mehr 
#
ROS_Publisher-Subscriber 
- In diesem Muster fungiert eine Komponente als Publisher, indem sie Daten zu einem bestimmten Thema (Topic) sendet. Andere Komponenten können sich als Subscriber für dieses Thema registrieren und die Daten empfangen. 
- Diese lose gekoppelte Kommunikation ermöglicht es den Komponenten, unabhängig voneinander zu arbeiten und auf Daten zuzugreifen, die sie benötigen. 
#
ROS_Client-Server 
>>>>>>> origin/main



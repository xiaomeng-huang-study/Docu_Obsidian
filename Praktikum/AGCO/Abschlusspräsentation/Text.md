#

# 
- Traditionale Landmaschinen werden durch Menschen gefahren und gesteuert. Um Arbeitskräfte zu sparen und präzisere Arbeitsabläufe zu erreichen, ist es notwendig, sie zu autonomen Maschinen umzuwandeln. 
- Ein typischer autonomer Prozess sieht so aus 

- spezifiziert für Bodenbearbeitung mit Traktor 
- Nach der Zuweisung der Aufgaben -> 
	- "Process Automation": stellt Parameter autonom ein, z.B. Pflug usw. 
	- "Local Guidance": erkennt und verfolgt Landmarke wie Schwade usw. 
- Dazu ist Sicherheit des Traktors wichtig 
	- z.B. Hindernisse nicht berühren, nicht zu einer nassen Stelle fahren 
- alle Ergebnisse der obigen Prozessen werden von "Health Management" geprüft. Wenn kein Problem, werden die Befehle durch Interface zu dem Traktor weitergeleitet. 

- Aus diesem System kann man leicht erkennen, Hindernis-Vermeidungssystem ist ein wichtiger Bestandteil. Meine Aufgabe ist, das Hindernis-Vermeidungssystem zu entwickeln und prüfen. Bevor das Programm auf echten Landmaschinen läuft, ist eine Simulation erforderlich. Deswegen geht es meine Arbeit hauptsächlich um Simulation. --> im roten Kästchen wird simuliertes System dargestellt. 

#
- um das System besser zu verstehen, schauen Sie bitte dies Bild. 

- Simulationsumgebung wird von Firma angeboten 
	- virtuelles Feld 
	- virtuelles Traktor-Modell 
	- virtueller LIDAR-Sensor (auf Traktor montiert) 
- Ich nehme die gesamte Simulationsumgebung auf und erweitere die. 
- Nach meiner Arbeit sollten folgende Ziele erreicht 
	- wenn ich einen vernünftigen Punkt eingebe, sollte das Traktor-Modell einen Pfad zum Endpunkt planen und verfolgen. 
	- während der Pfadverfolgung wird Hindernis vermeiden 

- Die vorgegebene kann man als "Input" verstehen, 
  die Ziele kann man als "Output" verstehen. 
  Die Bearbeitung zwischen den ist meine Arbeit. 

#
- Dazu muss man: 
	- einen Navigation-Stack anwenden  
		- für Pfadplanung und Pfadverfolgung zuständig
	- ein Collision-Avoidance Algorithmus entwickeln
		- für Hindernis-Vermeidung zuständig 

- Die zwei Teile bilden das Kontrolle-Modul 

#
- Kontrolle-Modul 
	- nimmt Rückmeldung aus Simulationsumgebung auf 
	- gibt Bewegungsbefehle aus 
	- --> Damit wird ein geschlossener Kreis gebildet 

#
- Arbeitspakete klar 
	- in 3 Phasen 
		- Vorbereitung 
		- Bearbeitung/ Entwicklung 
		- Integration 
	- Vorbereitung --> Inbetriebnahme 
		- Projektdateien der Simulation holen und die simulierte Umgebung wiederherstellen und erweitern 
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

# Architektur 
- Im Folgenden werde ich die Struktur des Systems näher erläutern 
- Unity 
	- 3 Sachen muss ich mindestens wiederherstellen 
	- Feld: Boden muss richtig gezeigt werden 
	- Traktor-Modell: nach den Bewegungsbefehlen präzise Bewegungen zeigen 
	- Sensor-Modell: simulierte Sensor-Daten können aus Sensor-Modell ausgeschickt 
- Collision-Avoidance 
	- die Positionsinfo und Sensordaten werden dem Algorithmus übergeben und verarbeitet 
	- Dann wird ein Navigationsziel berechnet und ausgeschickt 
- Navigation 
	- Nach Erhalt des Navigationsziels wird ein Pfad geplant 
	- dann mit der aktuellen Position mal vergleichen, und Bewegungsbefehlen ausgeben 
- 
#
- Bevor ich die Arbeitspakete einzeln durchgehe, ist es notwendig, das unterliegende System zu beschreiben. 
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

# Inbetriebnahme 
## Unity 
- zuerst muss ich die Umgebung in Unity wiederherstellen. 
### Unity-ROS-Connecter 
- Eine Brücke für den Nachrichtenaustausch muss gebaut werden 
- linke Seite ist Unity, rechte Seite ist ROS, jeder Nachrichtenaustausch findet durch die Brücke "Server Endpoint" statt. 
- ### Schnittstelle Bewegung 
- Das Traktor-Modell abonniert das Topic „/pilot/setpoint“  und zeigt Aktionen wie gerade nach vorne zu fahren und das Wenden, wenn es eine Nachricht erhält. 

# Navigation-Stack 
- Für Navigation-Stack habe ich "nav2" benutzt 
- 
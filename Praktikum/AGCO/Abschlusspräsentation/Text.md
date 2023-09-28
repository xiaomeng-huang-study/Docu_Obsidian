# 
Ich bin Xiaomeng Huang. Ich habe das Praxissemester im Zeitraum von Feb. bis Juli absolviert. Heute mache ich einen Vortrag dafür. 
# 
- Mein Praktikum war in Fendt (AGCO GmbH) 
- AGCO ist ein globaler Konzern in der Landtechnikbranche. Der Fokus liegt in der Entwicklung und Produktion von landwirtschaftlichen Geräten und Maschinen, die hauptsächlich im Agrarbereich eingesetzt werden. 
- Fendt ist ein Premiumhersteller von AGCO. 
- Ich habe in Abteilung Vorentwicklung gearbeitet.  
- Der Forschungsschwerpunkt liegt im Bereich der Autonomie, Agrarrobotik und alternativen Antrieben. 
---
- Autonomie hat mich sehr interessiert, daher habe ich das Praktikum in diese Richtung ausgerichtet. 
# 
- Traditionelle Landmaschinen werden durch Menschen gefahren und gesteuert. Um Arbeitskräfte zu sparen und präzisen Arbeitsablauf zu erreichen, ist es notwendig, sie zu autonomen Maschinen umzuwandeln. 
- Ein autonomer Prozess sieht so aus
- Sicherheit der Landmaschine kann man nicht vernachlässigen.
- Es ist notwendig, einen geeigneten Algorithmus zur Hindernisvermeidung zu entwickeln 
#
- Landmaschinen beziehen sich hier hauptsächlich auf Traktoren.
- Ich füge hier ein paar Bilder an. 
# 
- Meine Aufgabe ist, das Hindernis-Vermeidungssystem zu entwickeln und prüfen. 
- Bevor das Programm auf echten Landmaschinen läuft, ist eine Simulation erforderlich. Deswegen geht es meine Arbeit hauptsächlich um Simulation. 
---
- Simulationsumgebung wird von Firma angeboten 
	- virtuelles Feld 
	- virtuelles Traktor-Modell 
	- virtueller LIDAR-Sensor (auf Traktor montiert) 
- Ich nehme die gesamte Simulationsumgebung auf und erweitere die. 
---
- Nach meiner Arbeit sollten folgende Ziele erreicht 
	- wenn ich einen vernünftigen Punkt eingebe, sollte das Traktor-Modell einen Pfad zum Endpunkt planen und verfolgen. 
	- während der Pfadverfolgung wird Hindernis vermeiden 
---
- Die vorgegebene kann man als "Input" verstehen 
---
- die Ziele kann man als "Output" verstehen 
---
- Die Bearbeitung zwischen den ist meine Arbeit. 

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
# Hintergrund_ROS 
- Bevor ich die Arbeitspakete einzeln durchgehe, ist es notwendig, das unterliegende System zu beschreiben. 
- Hier werde ich Konzept für ROS einführen und die Kommunikationsmuster vorstellen 

- Modulare Architektur
	- Roboteranwendungen sind aus wiederverwendbaren und unabhängigen Komponenten aufzubauen. --> "ROS-Package" 
	- Kommunikation über definierte Schnittstellen 
- Kommunikation 
	- als Nächstes mehr erklären 
- Werkzeug und Bibliotheken 
	- Dazu gehören Tools zur Visualisierung, zum Debuggen, zur Simulation und zur Datenanalyse. 
	- Außerdem stehen eine breite Palette von Bibliotheken zur Verfügung, die Funktionen wie Pfadplanung, Lokalisierung, Bildverarbeitung und vieles mehr 
# ROS-Kommunikation 
- ROS hat 2 grundlegende Kommunikationsmuster 
## ROS_Publisher-Subscriber 
- In diesem Muster fungiert eine Komponente als Publisher, indem sie Daten zu einem bestimmten Thema (Topic) sendet. Andere Komponenten können sich als Subscriber für dieses Thema registrieren und die Daten empfangen. 
- Diese lose gekoppelte Kommunikation ermöglicht es den Komponenten, unabhängig voneinander zu arbeiten und auf Daten zuzugreifen, die sie benötigen. 
## ROS_Client-Server 
- 

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
- Damit das System richtig funktionieren kann, muss man die Eingabesanforderungen erfüllen. 
	- BT, Map, Sensor Daten 
	- tf-Kette 
- Innerhalb von diesem System spielen Controller-Server und Planner-Server wichtige Rollen. 
	- Der Planner-Server erstellt und optimiert Navigationspfade unter Verwendung verschiedener Algorithmen. Diese Pfade werden dann an den Controller-Server weitergegeben. 
	- Der Controller-Server vergleicht den Pfad mit der aktuellen Position und Ausrichtung, führt Korrekturen durch. Damit kann er Bewegungsbefehle generieren. 
	- grob zu sagen: Planner-Server ist für die globale Planung zuständig und Controller-Server ist für die Details zuständig. 
	- Deswegen muss man die 2 Controller anpassen 
- Ausgabe des Systems sind Bewegungsbefehle. 

## BT 
- 
## Sensor Daten 
- Die Form der Sensor Daten ist Pointcloud. Hier wird eine Ecke eines Würfels gezeigt. 
## Map 
- 
Die sind nicht der Schwerpunkt der Arbeit. 
## TF-Kette 
- Mein Hauptfokus liegt auf Transformationskette. 
- Zuerst müssen wir klären, was ist eine Transformation 
- z.B. ... Dann wird eine Transformation benötigt 
### Transformation 
- Hier wird eine Transformationsmatrix gezeigt. 
- Die besteht aus 2 Teilen 
	- a_11 bis a_33 ist eine Rotationsmatrix 
	- a_14 bis a_34 ist ein Translationsvektor 
#### Schauen wir zuerst Rotation an. 
Matrix ist vielleicht schwierig zu verstehen. Dazu gibt es auch eine andere Darstellungsform: Quaternion. 
Die sieht so aus. 
... 
#### Dann kommt Translation 
Die Bedeutung ist deutlich einfacher 

Dann ist die Definition für Transformation klar. ... 

### Frame 
Dazu wird Frame benötigt. 


### Motion-Model-Controller 
Hier muss ich Motion Model Controller vorstellen. 
- Der nimmt TF-Transformation und Steuerungsbefehle auf. 
	- z.B. die relative Position zwischen Traktor und Feld 
	- links rechts abbiegen, oder gerade nach vorne fahren. 
- Dann kommt eine zeitliche Integration der Geschwindigkeiten. 
- Und zum Schluss wird die neue Position und Ausrichtung bestimmt 

Die Firma hat die Umsetzung vom Erhalt der Bewegungsbefehle zu einer Aktualisierung der Transformation realisiert. Aber zu kompliziert, z.B. eine nichtlineare Geschwindigkeitsänderung. Um diesen Prinzip zu verstehen, ist Bicycle-Model Controller ein guter Einstiegspunkt. 
Setzen wir den Referenzpunkt auf Hinterachse, nach einigen mathematischen Herleitungen kann man die neue Ausrichtung und Position im Vergleich zu den vorherigen bestimmen. 
Hier kann man sehen, diskrete Integration wird verwendet. 

Nachdem alle Eingabeanforderungen erfüllt sind, müssen die zwei internen Server angepasst werden. Verschiedene Server können sich in Strategie oder Anwendungsbereich unterscheiden. 
Ein wichtiger Faktor ist die Unterstützung für verschiedene Bewegungsmodelle. 

- Omni Drive: das kann sich in alle Richtungen bewegen, ohne seine Ausrichtung zu ändern. Durch die unabhängige Steuerung der Räder kann der Roboter in beliebige Richtungen fahren. 
- Differential Drive: Das hat zwei Räder, die unabhängig voneinander gesteuert werden können. Die Geschwindigkeiten der beiden Räder können unterschiedlich sein, ist eine Drehung um seine eigene Achse möglich. 
- Ackermann Drive: Ein Ackermann Drive ist ein spezieller Typ von Differential Drive. Das verwendet eine spezielle Lenkgeometrie. Die Lenkungswinkel von den beiden Rädern sind unterschiedlich, d.h. Die Räder bewegen entlang von unterschiedlichen Kreisen. Deswegen ist eine präzise Kurvenfahrt möglich. 

Aus der obigen Darstellungen kann man sehen, verschiedene Type haben verschiedene Lenkungsarten. 
Nach der Parametereinstellung kann nav2 die entsprechenden Befehle für verschiedene Antriebstypen ausgeben. 

# Collision-Avoidance 
## Objekterkennung
- Die Firma hat ein Programm gestellt. Das Programm kann die PointClouds aufbauen, und die filtern, und schließlich die Informationen des erkannten Objekts als Polygon mit 4 Ecken in 2D-Ebene darstellen. 
- Von hier kann man die Koordinaten ablesen. Ich nehme ein Beispiel. Die Punkte sind mit diesen Koordinaten. 
- Zur Visualisierung bringen. Da in 2D-Ebene, wird die Höheinformation vernachlässigt. Ich nehme an, der Traktor richtet sich nach vorne. Deswegen ist das Objekt vor der linken Seite. 
## Algorithmus 
- Als nächstes werde ich über den Algorithmus sprechen. 
- Die Winkel dieser vier Punkte in Bezug auf den Traktor werden berechnet. 
- Dann erkenne ich 
	- dieser Punkt ist mit dem minimalen Winkel 
	- dieser Punkt ist mit dem maximalen Winkel 
- Danach markiere ich die 
- Der Traktor hat selbst eine Größe. Diese beiden Punkte werden um Sicherheitsradius nach außen erweitert. Der Sicherheitsradius kann 5 m usw. sein. Damit wird ein Hinderniswinkelbereich gebildet. (wie orange) 
- Als nächste wird mit dem Ziel verglichen. Dann wird in 2 Situationen aufgeteilt. 
	- Situation 1: Endziel nicht im Winkelbereich 
	- Situation 2: Endziel im Winkelbereich 
- Für Situation 1, einfach geradeaus in diese Richtung fahren. 
- Für Situation 2, wird die Fahrt verhindert. Muss man die Fahrt in Teilstrecken aufteilen. 
	- Auch mit diesem markierten Punkt wird um z.B. 2 mal Sicherheitsradius erweitern. Dann setze ich diesen Punkt als Zwischenstopp. 
	- Nachdem der Traktor diesen Punkt erreicht hat, werden die Hindernisinformationen erneut erfasst. Die gleiche Strategie wird erneut ausgeführt. 
	- d.h. Obiger Vorgang wird wiederholt bis Endziel erreicht wird. 
## Realisierung in ROS 
- Für die Realisierung in ROS habe ich eine Action, die vom Server "followwaypoints" angeboten wird, benutzt. Mit diesem Server werden angegebenen Punkte verfolgt. Damit habe ich eine volle Kontrolle bzw. eine Überwachung. 
- Ich, als Client, rufe diesen Dienst bzw. Service auf. Der Server wird von nav2 angeboten. Der Aufruf eines Dienstes kann man als Dialog verstehen. 

# Integration 
- Der letzte Schritt ist Integration. Das Programm, das ich geschrieben habe, muss mit den Programmen des Unternehmens zusammenarbeiten können. 
- Zur Veranschaulichung zeige ich ein Video 
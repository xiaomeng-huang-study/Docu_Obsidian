# SMART 
## Spezifisch 
- Weiterentwicklung einer Simulationsumgebung zur Fahrzeugbewegung 
- Integration von ROS2 Nav2 zur Navigation und Pfadverfolgung 
- Durchführung von Tests an einem autonomen System 

## Messbar 
Die Funktionalität wurde anhand von zwei zentralen **Kriterien** überprüft:
- Ob der simulierte **Traktor** den vom Nav2 geplanten Pfad **korrekt** und stabil **abfährt** 
- Ob **Hindernisse** im virtuellen Raum korrekt **erkannt** und sicher umfahren werden 

## Attraktiv 
Das Projekt hat einen hohen Praxisbezug zur **Entwicklung autonomer Fahrzeugen**. 
Die Fähigkeit, Fahrzeugbewegungen in einer realitätsnahen Simulation zu planen, umzusetzen und zu testen, ist ein essenzieller Baustein für das autonome Fahren. 

## Realistisch 
- **Unity** zur Visualisierung und Bewegungsdarstellung 
- **ROS2 mit Nav2** für Navigation und Pfadplanung 
- **C++ und Python** zur Entwicklung und Integration 
Die Simulationsumgebung verfügte über ein bestehendes **Interface**. D.h. die Simulation kann durch das Interface die ROS2-Nachrichten empfangen und daraufhin die Bewegung des Traktors in Unity entsprechend simulieren. 

## Terminiert 
- 6 Monaten 


# Fragen 
## ROS2-Kommunikation 
- Publisher-Subscriber 
- Client-Server 
- ``rqt_graph``, ``ros2 topic echo`` 

## Unity 
Da landwirtschaftliche Umgebungen oft komplex sind, kann „Unity“ die Umgebung besser simulieren als andere Werkzeuge wie „gazebo“, z. B. Grasflächen. 


## Herausforderungen 

- von Firma angeboten: Traktor-Modell, Simulationsumgebung (hier Bauerhof/ Feld)
- Hindernis vor dem Traktor legen, einen Endpunkt angeben --> Traktor-Modell kann einen Pfad zum Endpunkt planen und verfolgen. Während der Pfadverfolgung wird Hindernis vermieden.
- Dazu muss man: 
	- einen Navigation-Stack auswählen 
		- für Pfadplanung und Pfadverfolgung zuständig
	- ein Collision-Avoidance Algorithmus entwickeln
		- für Hindernis-Vermeidung zuständig 
- Der Kontrolle-Modul nimmt Rückmeldung aus Simulationsumgebung und gibt Bewegungsbefehle aus --> Damit wird ein geschlossener Kreis gebildet 


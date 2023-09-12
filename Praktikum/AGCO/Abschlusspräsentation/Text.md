- von Firma angeboten 
	- Simulationsumgebung 
		- Traktor-Modell 
		- Feld 
- Ziel 
	- Pfad zum Endpunkt in Echtzeit planen und verfolgen 
	- Hindernis vor dem Traktor-Modell während der Pfadverfolgung vermeiden 

- Dazu muss man: 
	- einen Navigation-Stack anwenden  
		- für Pfadplanung und Pfadverfolgung zuständig
	- ein Collision-Avoidance Algorithmus entwickeln
		- für Hindernis-Vermeidung zuständig 


- Kontrolle-Modul 
	- nimmt Rückmeldung aus Simulationsumgebung 
	- gibt Bewegungsbefehle aus 
	- --> Damit wird ein geschlossener Kreis gebildet 

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
		- 




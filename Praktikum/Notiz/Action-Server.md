- Action-Server
	- Definition 
		- ein Knoten, der auf eingehende Action-Anforderungen wartet und darauf reagiert, indem er eine Aktion ausführt und den Fortschritt der Ausführung an den Client zurückmeldet. 
	- Aufbau 
		- Ziel(goal) 
			- der gewünschte Endzustand der Aktion 
		- Feedback-Stream 
			- informiert den Client über den Fortschritt der Aktion 
		- Ergebnis(result)
			- ob die Aktion erfolgreich abgeschlossen 
	- Vorteile 
		- asynchrone Aktionen
			- Server kann während der Ausführung der Aktion weiterhin auf eingehende Anforderung reagieren und andere Aufgaben ausführen. 
		- Fortschrittüberwachung 
			- Fortschritt der Aktion in Echtzeit an den Client zurückmelden
			- nützlich für komplexe Aufgaben, die Zeit und Ressourcen erfordern. 
		- Modularität 
			- komplexe Aufgaben in kleinere Teilaufgaben unterteilen 
	- in nav2
		- communicate with the highest level BT navigator through `NavigatePose` 


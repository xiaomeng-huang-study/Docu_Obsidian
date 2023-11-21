# Begriffe 
- Padding 
	- Valid Padding: kein Padding hinzugefügt 
	- Same Padding: Padding am Rand füllen, damit die Ausgabe gleiche Größe wie Eingabe hat (wenn Stride = 1) 
- Stride 
	- Schrittweite, mit der der Filter (oder Kernel) über die Eingabe verschoben wird, wenn die Faltung durchgeführt wird. 

## Probleme 
- Overfitting 
	- Definition 
		- ein Modell während des Trainings zu gut auf die Trainingsdaten passt, aber Schwierigkeiten hat, auf neuen, nicht gesehenen Daten zu generalisieren 
	- Lösung 
		- [[Softwarearchitekturen/Notiz_Kapitel-2#^dropout-layer|Dropout-Layer]] 
		- [[Softwarearchitekturen/Notiz_Kapitel-2#^augmentierung|Augmentierung]] 
- Vanishing Gradients 
	- Definition 
		- die Gradienten der Verlustfunktion, die durch den Backpropagation-Algorithmus berechnet werden, in den tiefen Schichten des Netzwerks extrem klein werden. (Dies kann dazu führen, dass die Gewichtungen in diesen Schichten nicht effektiv aktualisiert werden, was das Training schwierig oder sogar unmöglich macht.) 
	- Lösungen 
		- ReLU-Aktivierungsfunktion verwenden 
		- [[Softwarearchitekturen/Notiz_Kapitel-2#^batch-norm|Batch-Normalization]] 


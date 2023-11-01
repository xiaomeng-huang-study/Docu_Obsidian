# Begriffe 
- Overfitting 
	- Definition: ein Modell während des Trainings zu gut auf die Trainingsdaten passt, aber Schwierigkeiten hat, auf neuen, nicht gesehenen Daten zu generalisieren 
- Padding 
	- Valid Padding: kein Padding hinzugefügt 
	- Same Padding: Padding am Rand füllen, damit die Ausgabe gleiche Größe wie Eingabe hat (wenn Stride = 1) 
- Stride 
	- Schrittweite, mit der der Filter (oder Kernel) über die Eingabe verschoben wird, wenn die Faltung durchgeführt wird. 

- Layer Typen 
	- Convolutional Layer (Conv Layer): Faltung mit einem Kernel 
	- Pooling Layer (Pooling Layer): reduziert die Dimensionalität der Feature-Maps 
		- Max-Pooling 
	- Fully Connected Layer (Dense Layer): die extrahierten Merkmalen zu klassifizieren 
	- Dropout Layer: zufällig einige Neuronen ausschalten, um Overfitting zu reduzieren 
	- Batch Normalization Layer: 


- Ausgabe Größe: $(n + 2p -f)/s + 1$ 
	- Füllen mit 1 Pixel am Rand (um 1 Pixel nach außen erweitern) $\Rightarrow$ p = 1 
	- Stride 1 $\Rightarrow$ s = 1 
	- Eingabe: n x n 
	- Filter: f x f 
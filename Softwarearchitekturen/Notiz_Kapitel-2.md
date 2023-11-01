# Begriffe 
- Overfitting 
	- Definition 
		- ein Modell während des Trainings zu gut auf die Trainingsdaten passt, aber Schwierigkeiten hat, auf neuen, nicht gesehenen Daten zu generalisieren 
	- Lösung 
		- [[Notiz_Kapitel-2#^dropout-layer|Dropout-Layer]] 
		- [[Notiz_Kapitel-2#^augmentierung|Augmentierung]]  
- Vanishing Gradients 
	- Definition 
		- die Gradienten der Verlustfunktion, die durch den Backpropagation-Algorithmus berechnet werden, in den tiefen Schichten des Netzwerks extrem klein werden. (Dies kann dazu führen, dass die Gewichtungen in diesen Schichten nicht effektiv aktualisiert werden, was das Training schwierig oder sogar unmöglich macht.) 
	- Lösungen 
		- ReLU-Aktivierungsfunktion verwenden 
		- [[Notiz_Kapitel-2#^batch-norm|Batch-Normalization]] 

- Augmentierung (data augmentation) ^augmentierung
	- Definition 
		- vorhandene Trainingsdaten zu modifizieren bzw. erweitern um die Menge der verfügbaren Trainingsdaten zu erhöhen und die Leistung und die Fähigkeit des Modells zur Generalisierung auf neue, nicht gesehene Daten zu verbessern 
- Padding 
	- Valid Padding: kein Padding hinzugefügt 
	- Same Padding: Padding am Rand füllen, damit die Ausgabe gleiche Größe wie Eingabe hat (wenn Stride = 1) 
- Stride 
	- Schrittweite, mit der der Filter (oder Kernel) über die Eingabe verschoben wird, wenn die Faltung durchgeführt wird. 

- Layer Typen 
	- Convolutional Layer (Conv Layer): Faltung mit einem Kernel 
	- Pooling Layer (Pooling Layer): reduziert die Dimensionalität der Feature-Maps 
		- Max-Pooling 
		- Average-Pooling 
	- Fully Connected Layer (Dense Layer): die extrahierten Merkmalen zu klassifizieren 
	- Dropout Layer : zufällig einige Neuronen ausschalten, um Overfitting zu reduzieren ^dropout-layer
	- Batch Normalization Layer: um die Aktivierung eines Neurons normalisiert zu halten. ^batch-norm
		- Training beschleunigen 
		- Fähigkeiten des Modells verbessern 


- Ausgabe Größe: $(n + 2p -f)/s + 1$ 
	- Füllen mit 1 Pixel am Rand (um 1 Pixel nach außen erweitern) $\Rightarrow$ p = 1 
	- Stride 1 $\Rightarrow$ s = 1 
	- Eingabe: n x n 
	- Filter: f x f 

- Unterschied zwischen Alex-Net und Le-Net5 
	- Anzahl der Parameter 
	- Auflösung 
		- Le-Net: für kleinere Eingabeauflösungen (32 x 32) 
		- Alex-Net: für größere Eingabeauflösungen (227 x 227) 
	- Aktivierungsfunktion 
		- Le-Net: Sigmoid 
		- Alex-Net: Relu 
			- schnellere Konvergenz 
			- Reduktion der "Vanishing Gradients" 
	- Tiefe des Netzes 
		- Le-Net: mit wenigen Schichten (2 Convolutional-Schichten + 3 Fully Connected-Schichten) 
		- Alex-Net: mit mehreren Schichten (5 Convolutional-Schichten + 3 Fully Connected-Schichten) 
			- tiefere Merkmalsextraktion und bessere Modellierung von Bildmerkmalen. 
	- Anzahl der Ausgabeklassen 
		- Le-Net: wenige Ausgabeklassen 
		- Alex-Net: 1000 Ausgabeklassen 
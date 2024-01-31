# Begriffe 
- Padding 
	- Valid Padding: kein Padding hinzugefügt 
	- Same Padding: Padding am Rand füllen, damit die Ausgabe gleiche Größe wie Eingabe hat (wenn Stride = 1) 
- Stride 
	- Schrittweite, mit der der Filter (oder Kernel) über die Eingabe verschoben wird, wenn die Faltung durchgeführt wird. 


# Animation 
- Convolution 
	- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-04_22-49-00.gif?raw=" width="600" /> 


# Probleme 
- Overfitting 
	- Definition 
		- ein Modell während des Trainings zu gut auf die Trainingsdaten passt, aber Schwierigkeiten hat, auf neuen, nicht gesehenen Daten zu generalisieren 
	- Lösung 
		- Dropout-Layer 
		- Augmentierung 
- Vanishing Gradients 
	- Definition 
		- die Gradienten der Verlustfunktion, die durch den Backpropagation-Algorithmus berechnet werden, in den tiefen Schichten des Netzwerks extrem klein werden. (Dies kann dazu führen, dass die Gewichtungen in diesen Schichten nicht effektiv aktualisiert werden, was das Training schwierig oder sogar unmöglich macht.) 
	- Lösungen 
		- ReLU-Aktivierungsfunktion verwenden 
		- Batch-Normalization 


# Wichtige Größen
- ==Ausgabe Größe==: $(n + 2p -f)/s + 1$ 
	- Padding: Füllen mit 1 Pixel am Rand (um 1 Pixel nach außen erweitern) $\Rightarrow$ p = 1 
	- Stride 1 $\Rightarrow$ s = 1 
	- Eingabe: n x n 
	- Filter: f x f 
- Recheneigenschaften 
	- ==Anzahl der Parameter== [(hilfreiche Erklärung)](https://stackoverflow.com/questions/42786717/how-to-calculate-the-number-of-parameters-for-convolutional-neural-network ) 
		- Input-Layer: 0 
		- Convolutional layers 
			- (Anzahl der Filter) x (Volumen der Filter + 1)
				- Volumen der Filter = (Filter Höhe) x (Filter Breite) x (Anzahl der Kanäle in Eingabe)
				- "+ 1": für den Bias-Term pro Filter 
			- eng.: (Number of Kernel) x (Kernel Volume + 1) 
		- Pooling layers: 0, aber 2 Hyperparameter: $f$ und $s$ 
		- Fully-connected layers 
			- (Eingabegröße) x (Ausgabegröße) + Ausgabegröße 
				- "+ Ausgabegröße": für den Bias-Term pro Ausgabe 
			- eng.: (Input Size) x (Output Size) + Output Size 
	- ==Speicherbedarf== 
		- Convolutional layers (Ausgaben verbraucht den meisten Speicherplatz) 
			- (Batch Size) x (Ausgabevolumen) x (Präzision) 
				- Präzision: z.B. float32 -> 32 Bit / dig. 
		- Fully connected layers (Parameter verbraucht den meisten Speicherplatz) 
			- (Batch Size) x (Anzahl der Parameter) x (Präzision)
	- ==Flops== (i.d.R. 1 MAC = 2 Flops)
		- Convolutional layers 
			- (Volumen der Filter) x 2 x (Ausgabefläche) x (Anzahl der Filter) 
			- eng.: 2 x (Number of Kernel) x (Kernel Volume) x (Output area) 
		- Fully connected layers 
			- 2 x (Eingabegröße) x (Ausgabegröße) 
				- (beide sind 1-dimensional) 
			- eng.: 2 x (Input Size) x (Output Size) 
	- Eigenschaften 
		- Anzahl der Parameter: voll verknüpfte Schichten > Faltungsschichten 
		- Rechenaufwand (Flops): Faltungsschichten >> voll verknüpfte Schichten 
	- Anmerkungen 
		- Filter = Kernel 
		- Anzahl der Kanäle in Eingabe = Anzahl der Kanäle pro Filter 
		- Anzahl der Filter = Anzahl der Ausgabeklassen 

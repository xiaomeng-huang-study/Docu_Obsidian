# Begriffe 
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

- Padding 
	- Valid Padding: kein Padding hinzugefügt 
	- Same Padding: Padding am Rand füllen, damit die Ausgabe gleiche Größe wie Eingabe hat (wenn Stride = 1) 
- Stride 
	- Schrittweite, mit der der Filter (oder Kernel) über die Eingabe verschoben wird, wenn die Faltung durchgeführt wird. 

# CNN (Convolutional Neural Network) 
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

- ==Ausgabe Größe==: $(n + 2p -f)/s + 1$ 
	- Padding: Füllen mit 1 Pixel am Rand (um 1 Pixel nach außen erweitern) $\Rightarrow$ p = 1 
	- Stride 1 $\Rightarrow$ s = 1 
	- Eingabe: n x n 
	- Filter: f x f 
- Recheneigenschaften 
	- ==Anzahl der Parameter== [(hilfreiche Erklärung)](https://stackoverflow.com/questions/42786717/how-to-calculate-the-number-of-parameters-for-convolutional-neural-network ) 
		- Input-Layer: 0 
		- Convolutional layers 
			- (Anzahl der Filter) x (Volumen der Filter) + Anzahl der Filter 
				- Volumen der Filter = (Filter Höhe) x (Filter Breite) x (Anzahl der Kanäle in Eingabe)
				- "+ Anzahl der Filter": für den Bias-Term pro Filter 
			- eng.: (Number of Kernel) x (Kernel Shape) + Number of Kernel 
		- Pooling layers: 0 
		- Fully-connected layers 
			- (Eingabegröße) x (Ausgabegröße) + Ausgabegröße 
				- "+ Ausgabegröße": für den Bias-Term pro Ausgabe 
			- eng.: (Input Size) x (Output Size) + Output Size 
	- Speicherbedarf 
		- Batchsize x Anzahl der Parameter x Präzision 
			- Präzision: z.B. float32 -> 32 
	- ==Flops== 
		- Convolutional layers 
			- 2 x (Anzahl der Filter) x (Volumen der Filter) x (Ausgabegröße) 
			- eng.: 2 x Number of Kernel x Kernel Shape x Output Shape 
		- Fully connected layers 
			- 2 x (Eingabegröße) x (Ausgabegröße) 
			- eng.: 2 x Input Size x Output Size 
	- Eigenschaften 
		- Anzahl der Parameter: voll verknüpfte Schichten > Faltungsschichten 
		- Rechenaufwand (Flops): Faltungsschichten >> voll verknüpfte Schichten 
	- Anmerkungen 
		- Filter = Kernel 
		- Anzahl der Kanäle in Eingabe = Anzahl der Kanäle pro Filter 
		- Anzahl der Filter = Anzahl der Ausgabeklassen 
		- Beschreibung für 1-Dimension: "Größe" / "Size" ; für mehr-Dimension : "Volumen" / "Size" 

- Einschub 
	- Data augmentation ^augmentierung
		- Definition 
			- vorhandene Trainingsdaten zu modifizieren bzw. erweitern um die Menge der verfügbaren Trainingsdaten zu erhöhen und die Leistung und die Fähigkeit des Modells zur Generalisierung auf neue, nicht gesehene Daten zu verbessern 
		- Type 
			- Crop 
			- Flip 
			- Translation 
			- Rotation 
			- Zoom 
			- Contrast 
			- Brightness 

- Initialisierung der Gewichte 
	- Schaubild: ![](https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-09_11-15-21.png?raw=) 
	- Initialisierung zu klein 
		- Die Aktivierungen sind hauptsächlich um 0 herum verteilt 
			- Aktivierungen (bei -1 und 1) -> 0 $\Rightarrow$ Gradients -> 0 
	- Initialisierung zu groß 
		- Die Aktivierungen sind hauptsächlich um 0 und 1 herum verteilt 
			- Gradients bei 0 und 1 (z.B. für tanh, sigmoid) -> 0
	- Initialisierung geeignet 

- moderne CNNs 
	- Alex-Net 
		- Schaubild: ![|200](https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-09_15-52-00.png?raw=) 
		- Merkmale 
			- erstes tiefes CNN und führte ReLU und Dropout ein 
	- ZF-Net 
		- Schaubild: ![](https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-09_15-54-38.png?raw=) 
		- Merkmale 
			- betonte die Bedeutung der Merkmalsrepräsentation in frühen Schichten 
	- VGG 
		- Schaubild: ![|250](https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-10_16-19-33.png?raw=)
		- Merkmale 
			- eine sehr tiefe Architektur und die Verwendung von kleinen 3x3-Filtern 
			- Transfer Learning 
				- Transfer Learning ist eine Methode des maschinellen Lernens, bei der ein Modell, das auf eine Aufgabe trainiert wurde, auf eine andere, oft verwandte Aufgabe angewendet wird. Im Transfer Learning werden die Kenntnisse und Merkmale, die das Modell bei der ersten Aufgabe gelernt hat, genutzt, um die Leistung bei der neuen Aufgabe zu verbessern.


## Q&A 
- Warum ist Eingabe bei Alex-Net tatsächlich 227x227 nicht 224x224? 
	- geg.: 1.conv-layer Output Shape: 55 x 55 $\Rightarrow$ Aus. = 55 
	- Aus. = (n + 2p - f) / s + 1 $\Rightarrow$ n = (Aus. -1) x s + f - 2p 
	- $\Longrightarrow$ (55 - 1) x 4 + 11 - 0 = 227 
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

## Beispiel 
- code 
	```python
	# define cnn model
	def define_model():
	    model = keras.models.Sequential()
	    model.add(keras.layers.Resizing(227, 227, interpolation="bilinear", crop_to_aspect_ratio=False))
	    model.add(keras.layers.Conv2D(filters=96, kernel_size=(11,11), strides=(4,4), activation='relu', input_shape=(227,227,3)))
	    model.add(keras.layers.MaxPool2D(pool_size=(3,3), strides=(2,2)))
	    model.add(keras.layers.Conv2D(filters=256, kernel_size=(5,5), strides=(1,1), activation='relu', padding="same"))
	    model.add(keras.layers.MaxPool2D(pool_size=(3,3), strides=(2,2)))
	    model.add(keras.layers.Conv2D(filters=384, kernel_size=(3,3), strides=(1,1), activation='relu', padding="same"))
	    model.add(keras.layers.Conv2D(filters=384, kernel_size=(1,1), strides=(1,1), activation='relu', padding="same"))
	    model.add(keras.layers.Conv2D(filters=256, kernel_size=(1,1), strides=(1,1), activation='relu', padding="same"))
	    model.add(keras.layers.MaxPool2D(pool_size=(3,3), strides=(2,2)))
	    model.add(keras.layers.Flatten())
	    model.add(keras.layers.Dense(4096, activation='relu'))
	    model.add(keras.layers.Dropout(0.5))
	    model.add(keras.layers.Dense(4096, activation='relu'))
	    model.add(keras.layers.Dropout(0.5))
	    model.add(keras.layers.Dense(10, activation='softmax'))
	    # compile model
	    opt = keras.optimizers.SGD(learning_rate=0.001, momentum=0.9)
	    model.compile(optimizer=opt, loss='sparse_categorical_crossentropy', metrics=['accuracy'])
	
	    model.build(input_shape=(None, 227,227,3)) # `input_shape` is the shape of the input data, e.g. input_shape = (None, 32, 32, 3)
	    #summary of the model
	    #Can you calculate the number of parameters for each layer?
	    #How many parameters has the first convolutional layer?
	    #Answer: 34944 = 11 * 11 * 3 * 96 + 96
	    model.summary()
	    return model
	
	# entry point, run the test harness
	history, model = run_test_harness()
	```
- Ergebnis: ![|625](https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-01_16-27-03.png?raw=)
- Rechenbeispiel 
	- Conv-Layer 1 
		- Ausgabegröße 
			- Eingabe 227 x 227 $\rightarrow$ n = 227 
			- no Padding $\rightarrow$ p = 0
			- Filter: 11 x 11 $\rightarrow$ f = 11 
			- Stride s = 4 
			- $\Rightarrow$ (227 - 11) / 4 + 1 = 55 
			- Anzahl der Filter = 96 $\Rightarrow$ Ausgabeklasse = 96 
			- $\Longrightarrow$ 55 x 55 x 96 
		- Anzahl der Parameter 
			- Filter 11 x 11 
			- Kanäle in Eingabe 3 
			- Anzahl der Filter 96 
			- $\Longrightarrow$ 96 x 11 x 11 x 3 + 96 = 34944 
		- Speicherbedarf 
			- Batch Size 16 
			- Präzision KB 
			- $\Longrightarrow$ 16 x 34944 / (8 x 1000) = 69.888 KB 


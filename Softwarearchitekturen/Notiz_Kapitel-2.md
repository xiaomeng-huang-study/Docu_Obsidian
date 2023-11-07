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

- Augmentierung (data augmentation) ^augmentierung
	- Definition 
		- vorhandene Trainingsdaten zu modifizieren bzw. erweitern um die Menge der verfügbaren Trainingsdaten zu erhöhen und die Leistung und die Fähigkeit des Modells zur Generalisierung auf neue, nicht gesehene Daten zu verbessern 

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

- Anzahl der Parameter 
	- (Anzahl der Filter) x (Filter Höhe) x (Filter Breite) x (Anzahl der Kanäle) + Anzahl der Filter 
		- + Anzahl der Filter: für den Bias-Term pro Filter 
- Speicherbedarf 
	- (Batch Size) x (Anzahl der Parameter) x (Präzision) 
		- Präzision: float32 -> 32 
- Ausgabe Größe: $(n + 2p -f)/s + 1$ 
	- Padding: Füllen mit 1 Pixel am Rand (um 1 Pixel nach außen erweitern) $\Rightarrow$ p = 1 
	- Stride 1 $\Rightarrow$ s = 1 
	- Eingabe: n x n 
	- Filter: f x f 
- Anmerkungen 
	- Anzahl der Kanäle in Eingabe = Anzahl der Kanäle pro Filter 
	- Anzahl der Filter = Anzahl der Ausgabeklassen 

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

# Code 
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
- ![|625](https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-01_16-27-03.png?raw=)
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
		- Rechenaufwand 
			- (3 x 11 x 11 + 55 x 55) x 96 

- Problem: immer wenigere Aktivierungen in den hinteren Schichten. -> die Daten für hintere schlecht zu trainieren. 
- 
# Batch Normalization 
- Verlauf 
	- Schaubild: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-20_21-49-35.png?raw=" width="500" /> 
	- $\beta$ und $\gamma$ sind lernbare Parameter 
	- $\mu_{mov}$ und $\sigma_{mov}$ sind gespeicherte Parameter 
	- $\alpha$ ist ein vorgegebenes Gewicht für Vergangenheit und aktuelle 
	- Moving Average 
		- der während des Trainings dazu dient, stabile Schätzungen des Mittelwerts und der Standardabweichung der Aktivierungen über mehrere Mini-Batches zu erhalten 
- Algorithmus 
	- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-20_21-56-14.png?raw=" width="350" /> 
- Funktionen 
	- die Konvergenzgeschwindigkeit zu verbessern 
	- die Genauigkeit zu verbessern 
	- Schaubild: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-20_21-46-53.png?raw=" width="400" /> 
		- Kurve ist nach links (Konvergenzgeschwindigkeit) und oben (Genauigkeit) verschoben 


# Dropout-Layer
- zufällig einige Neuronen ausschalten 
- um Overfitting zu reduzieren


# Data augmentation 
- vorhandene Trainingsdaten zu modifizieren bzw. erweitern 
- um die Menge der verfügbaren Trainingsdaten zu erhöhen und die Leistung und die Fähigkeit des Modells zur Generalisierung auf neue, nicht gesehene Daten zu verbessern 
- Type 
	- Crop 
	- Flip 
	- Translation 
	- Rotation 
	- Zoom 
	- Contrast 
	- Brightness 
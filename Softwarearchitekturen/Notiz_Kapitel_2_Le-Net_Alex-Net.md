# Le-Net
- Schaubild: <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-09_15-50-10.png?raw=" width="200" /> 


# Alex-Net
- Schaubild: <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-09_15-52-00.png?raw=" width="200" /> 
- Layer Typen 
	- Convolutional Layer (Conv Layer): Faltung mit Kernel 
	- Pooling Layer (Pooling Layer): reduziert die Dimensionalität der Feature-Maps 
		- Max-Pooling 
		- Average-Pooling 
	- Fully Connected Layer (Dense Layer): die extrahierten Merkmalen zu klassifizieren 
- Merkmale 
	- erstes tiefes CNN und führte ReLu ein 

## Q&A 
- Warum ist Eingabe bei Alex-Net tatsächlich 227x227 nicht 224x224? 
	- geg.: 1.conv-layer Output Shape: 55 x 55 $\Rightarrow$ Aus. = 55 
	- Aus. = (n + 2p - f) / s + 1 $\Rightarrow$ n = (Aus. -1) x s + f - 2p 
	- $\Longrightarrow$ (55 - 1) x 4 + 11 - 0 = 227 

# Vergleich von Le-Net und Alex-Net
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
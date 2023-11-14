- Deformation 形变 
- stimulate 刺激,激励 
- inhibit 抑制 

- Herausforderungen für KI 
	- Verzerrungen 
	- Blackbox 
	- unbekannte 
	- nicht Bild, sondern Pixel 
	- Viewpoint 
	- Beleuchtung 
	- Deformation 
	- Verdeckung 
	- Background 
	- Variation innerhalb einer Klasse 

- examples unlabeled: unsupervised machine learning 
- examples labeled: Clustering (Grouping unlabeled examples) 

- learning rate: ![](https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Learning-rate.png?raw=)  
- epoch: Vorwärtsdurchlauf + Rückwärtsdurchlauf 
- Backpropagation 反向传播算法 
	- Verlauf 
		- 1) Vorwärtsdurchlauf (Forward Pass) 
		- 2) Berechnung des Fehlers (Loss) 
		- 3) Rückwärtsdurchlauf (Backward Pass) 
		- 4) Partielle Ableitungen mit dem Kettenregel (Chain Rule) 
		- 5) Aktualisierung des Gewichtsparameter 

- Multi-Layer-Perzeptron 
	- Schaubild: ![|400](https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-10-20_22-18-09.png?raw=) 
	- Dimensionen: 
		- input_size = 2 
		- 1 hidden layer 
		- hidden size = 5 (5 hidden neurons) 
		- output_size = 1 
	- Code Beispiel 
		```python
		def demo_MLP(input, label, epochs, learning_rate):
		    # extend to matrix (num_smaples,1)
		    label = np.expand_dims(label, axis=1)
		
		    # Gewichtsmatrizen und Bias-Vektoren für jede Schicht
		    input_size = input.shape[1] # e.g. 2
		    hidden_size = 5  
		    output_size = 1
		
		    W1 = np.random.randn(input_size, hidden_size) # e.g. (2, 5)
		    b1 = np.random.randn(hidden_size)             # e.g. (5)
		    W2 = np.random.randn(hidden_size, output_size)# e.g. (5,1)
		    b2 = np.random.randn(output_size)             # e.g. (1)
		
		    for epoch in range(epochs):
		        # Vorwärtsdurchlauf
		        hidden_layer = sigmoid(np.dot(input, W1) + b1)
		        output_layer = sigmoid(np.dot(hidden_layer, W2) + b2)
		        y_pred = output_layer
		
		        # Berechnung des Fehlers (MSE)
		        loss = mse_loss(y, y_pred)
		
		        # Berechnung der Gradienten
		        output_delta = 2 * (y_pred - y) * sigmoid_derivative(y_pred)
		        hidden_delta = np.dot(output_delta, W2.T) * sigmoid_derivative(hidden_layer)
		
		        # Aktualisierung der Gewichte und Bias-Vektoren
		        W2 -= learning_rate * np.dot(hidden_layer.T, output_delta)
		        b2 -= learning_rate * np.sum(output_delta, axis=0)
		        W1 -= learning_rate * np.dot(input.T, hidden_delta)
		        b1 -= learning_rate * np.sum(hidden_delta, axis=0)
		
		    return W1, b1, W2, b2
		```

- Deep Learning: 
	- Prozess 
		- Schaubild: siehe S91 
	- Input $X$ 
		- als Tensoren 
			- Vector data (Rank-2 Tensor): (samples, features) 
				- samples -> Beispiele 
				- features -> Merkmale 
			- Timeseries data or sequence data (Rank-3 Tensor): (samples, timesteps, features) 
			- Images (Rank-4 Tensor): (samples, height, width, channels) 
				- channels -> RGB
			- Videos (Rank-5 Tensor): (samples, frames, height, width, channels) 
	- Batch 
		- Definition: Teilmenge von Trainingsdaten, gemeinsam zum Trainieren verwendet 
		- Vorteile 
			- Effizienz 
			- Speicherplatz 
			- Stochastizität 
		- als ein Hyperparameter 
	- Layers 

- Normalisierung: 

- Vertauschung: Zahl in Kästchen in lila groß 


- Optimizer 
	- Funktion: die Gewichtungen eines neuronalen Netzwerks anzupassen, und die Loss-Score zu minimieren 
	- Typen 
		- SGD (Stochastic Gradient Descent) 随机梯度下降 
			- berechnet den Gradienten der Verlustfunktion für eine kleine Stichprobe (Minibatch) 
		- SGD mit Momentum 
			- kombiniert den aktuellen Gradienten mit einer gewichteten Summe der vorherigen Gradienten -> beschleunigt die Anpassung der Gewichtungen 
		- AdaGrad (Adaptive Gradient) 
			- basiert auf der bisherigen Gradientenhistorie 
				- stark aktualisierte Gewichtungen -> geringere Lernrate 
			- 
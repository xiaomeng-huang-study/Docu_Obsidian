# Vocabulary 
- Deformation 形变 
- stimulate 刺激,激励 
- inhibit 抑制 


# KI 
- Typen 
	- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-01-13_14-58-15.png?raw=" width="400" /> 
	- Künstliche Intelligenz (KI, engl. Artificial Intelligence): bezieht sich auf die Fähigkeit von Computern oder Maschinen, Aufgaben auszuführen, die normalerweise menschliche Intelligenz erfordern. 
	- Maschinelles Lernen (ML, engl. Machine Learning): ist ein Teilgebiet der künstlichen Intelligenz, das sich auf die Entwicklung von <u>Algorithmen</u> konzentriert, die es Computern ermöglichen, aus Daten zu lernen. 
	- Überwachtes Lernen (engl. Supervised Learning): Bei überwachtem Lernen werden Algorithmen auf Grundlage von <u>gelabelten</u> Trainingsdaten trainiert. 
	- Unüberwachtes Lernen (engl. Unsupervised Learning): Im unüberwachten Lernen werden Algorithmen mit <u>nicht gelabelten</u> Daten trainiert. 
	- Tiefes Lernen (engl. Deep Learning): Tiefes Lernen bezieht sich auf den Einsatz von <u>neuronalen Netzwerken</u> mit vielen Schichten (tiefe Netzwerke), um komplexe Aufgaben zu lösen. 
	- Verstärkungslernen (engl. Reinforcement Learning): Bei Verstärkungslernen wird ein Agent in einer Umgebung platziert und lernt, Aktionen auszuführen, um eine Belohnung zu maximieren. Das System trifft Entscheidungen basierend auf <u>Feedback</u> in Form von <u>Belohnungen oder Strafen</u>. 
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


# Neuronales Netz 
- learning rate: ![](https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Learning-rate.png?raw=)  

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


# Deep Learning 
- Einführung 
	- Daten 
		- train - validation - test 
	- Prozess 
		- Einfaches Schaubild: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-21_16-29-26.png?raw=" width="450" /> 
		- Verlauf 
			- 1) Vorwärtsdurchlauf (Forward Pass) 
			- 2) Berechnung des Fehlers (Loss) 
			- 3) Rückwärtsdurchlauf (Backward Pass) 
			- 4) Partielle Ableitungen mit dem Kettenregel (Chain Rule) 
			- 5) Aktualisierung des Gewichtsparameter 
		- epoch: Vorwärtsdurchlauf + Rückwärtsdurchlauf 
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
	- Layer 
		- eine Schicht von Neuronen oder Neuronenverbindungen in einem neuronalen Netzwerk 
		- Typen 
			- Fully-Connected-Layer 
			- Convolutional-Layer 
			- Pooling-Layer 
			- Recurrent-Layer 
			- Normalization-Layer 
		- Aktivierungsfunktion 
			- Jedes Neuron in einem Layer hat eine Aktivierungsfunktion 
			- nicht lineare Beziehungen zu lernen 
			- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-21_16-33-31.png?raw=" width="500" /> 
		- Initialisierung 
			- Schaubild: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-09_11-15-21.png?raw=" width="600" /> 
			- Initialisierung zu klein 
				- Die Aktivierungen sind hauptsächlich um 0 herum verteilt 
					- Aktivierungen (bei -1 und 1) -> 0 $\Rightarrow$ Gradients -> 0 
			- Initialisierung zu groß 
				- Die Aktivierungen sind hauptsächlich um 0 und 1 herum verteilt 
					- Gradients bei 0 und 1 (z.B. für tanh, sigmoid) -> 0
			- Initialisierung geeignet 
	- Weights 
		- Fully-Connected-Layer: Gewichtungsmatrix + Bias 
		- Convolutional-Layer: Gewichtungsmatrix + Bias 
		- Pooling-Layer: keine lernbaren Parameter 
	- Predictions 
		- Klassifikation z.B. 80% A, 20% B 
		- Regression z.B. die Kosten 3000 Euro 
		- Textgenerierung 
		- Anomalie-Erkennung 
		- Objekterkennung 
		- Sprachübersetzung 
	- Loss-Funktion / Kosten-Funktion 
		- Einschub: Log-Wahrscheinlichkeit 
			- manchmal sind die Wahrscheinlichkeiten extrem winzig oder sehr nahe bei 1, problematisch mit begrenzter nummerischer Präzision auf einem Computer 
		- Mean-Squared-Error (MSE) 
			- bei Regressionsproblemen verwendet, Output ist eine kontinuierliche Zahl 
			- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-01-13_22-46-11.png?raw=" width="500" /> 
		- Binary-Cross-Entropy (BCE) 
			- bei binären Klassifikationsproblemen 
			- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-01-13_22-47-11.png?raw=" width="650" /> 
		- Categorical-Cross-Entropy (CCE) 
			- bei Multi-Klassen Klassifikationsproblemen 
			- One-Hot-Encoding 
			- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-01-13_22-48-49.png?raw=" width="500" /> 
		- Sparse-Categorical-Cross-Entropy (SCCE) 
			- bei Multi-Klassen Klassifikationsproblemen 
			- nicht One-Hot-Encoding 
			- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-01-13_22-51-28.png?raw=" width="500" /> 
	- Optimizer 
		- Funktion: die <u>Gewichtungen</u> eines neuronalen Netzwerks anzupassen, und die <u>Loss-Score</u> zu minimieren 
		- Typen 
			- Stochastic Gradient Descent (SGD) 随机梯度下降 
				- berechnet den Gradienten der Verlustfunktion für eine kleine Stichprobe (Minibatch) 
			- SGD mit Momentum 
				- kombiniert den aktuellen Gradienten mit einer gewichteten Summe der vorherigen Gradienten -> beschleunigt die Anpassung der Gewichtungen 
			- Adaptive Gradient (AdaGrad) 
				- basiert auf der bisherigen Gradientenhistorie 
					- stark aktualisierte Gewichtungen -> geringere Lernrate 
			- Root Mean Square Propagation (RMSprop) 
				- ähnlich wie Adagrad, aber mit einer exponentiell abnehmenden Durchschnittfunktion für die vergangenen Gradienten 
			- Adaptive Moment Estimation (Adam) 
				- kombiniert Ideen aus Momentum und RMSprop 
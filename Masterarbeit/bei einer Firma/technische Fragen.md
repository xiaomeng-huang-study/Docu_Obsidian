# Machine Learning 


# Pytorch 
## Grundbegriffe 
- Tensor: multi-dimensionale Array-Struktur 
- Autograd: das automatische Differenzierungsmodul, das die Gradienten für Backpropagation berechnet. 
- Model: ein neuronales Netz als Klasse, die von `nn.Module` erbt 
- Loss Function: die misst, wie gut oder schlecht das Modell ist. 
- Optimizer: aktualisiert die Gewichte im Modell basierend auf den Gradienten 
- Dropout: 
- Batch-Normalization: Verschiebung der Ausgabe einer Schichte $\rightarrow$ normalisiert die Verteilung, um die Eingaben für nachfolgende Schichten stabiler und konsistenter zu machen. 

## Typische Interviewfragen 
### Wie sieht ein typischer Trainingsablauf in PyTorch aus? 
- Voraussetzung: Modell, Loss-Funktion, Optimierer 
- Vorwärtsdurchlauf $\rightarrow$ Loss berechnen $\rightarrow$ Backpropagation $\rightarrow$ Update der Gewichte 

## Was ist der Unterschied zwischen `model.eval()` und `model.train()`? 
- `model.train()` aktiviert bestimmte Layer wie Dropout oder BatchNorm für das Training.  
- `model.eval()` deaktiviert sie, um konsistente Ergebnisse beim Testen oder Inferenz zu bekommen. 

### Wann benutzt man `torch.no_grad()`? 
- nur Vorhersagen macht 


# Scikit-Learn 
## Grundbegriffe 
- Estimator: Alles, was `.fit()` kann, ist ein Estimator 
- Transformer: Objekte, die Daten transformieren können 
- Predictor: Ein Estimator mit einer `.predict()`-Methode. 
- Pipeline: Eine verkettete Abfolge von Transformations- und Modellierungsschritten 
- Cross-Validation: Technik zur Bewertung eines Modells durch Aufteilen der Daten in Trainings- und Testteile in mehreren Durchgängen 
- Hyperparameter: Parameter, die das Verhalten des Modells vor dem Training steuern 
- GridSearchCV: Werkzeuge zur automatisierten Suche nach den besten Hyperparametern mit Cross-Validation 

## Typische Fragen 
### Was ist der Unterschied zwischen `.fit()`, `.transform()` und `.fit_transform()`? 
- `.fit()` berechnet die notwendigen Parameter aus den Trainingsdaten, z. B. Mittelwert und Standardabweichung bei einem `StandardScaler`.  
- `.transform()` wendet diese Parameter auf die Daten an.  
- `.fit_transform()` kombiniert beide Schritte und wird oft direkt auf die Trainingsdaten angewendet. 

### Wie funktioniert eine Pipeline in scikit-learn und warum ist sie nützlich? 

### Was ist Cross-Validation und warum sollte man sie verwenden? 
- Cross-Validation ist eine Methode zur Bewertung eines Modells, indem die Daten in mehrere Trainings- und Testsets aufgeteilt werden. 
- um Overfitting zu reduzieren 

### Wie würden Sie Features skalieren und warum ist das wichtig für bestimmte Modelle? 
- Man kann `StandardScaler` oder `MinMaxScaler` verwenden. 
- empfindlich auf die Größenordnung 


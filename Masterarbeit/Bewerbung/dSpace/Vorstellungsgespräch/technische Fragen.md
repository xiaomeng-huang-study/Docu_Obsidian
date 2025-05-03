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


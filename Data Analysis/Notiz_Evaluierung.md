# Evaluierung 
## Holdout-Method 
- Datensatz wird in zwei Teile aufgeteilt: ein Trainingsset und ein Testset. 

## Kreuzvalidierung (Cross-Validation) 
- Der Datensatz k-fache Kreuzvalidierung wird in k gleich große Teile (Falten) aufgeteilt. Das Modell wird k Mal trainiert und getestet, wobei jedes Mal eine andere Falte als Testset und die restlichen k-1 Falten als Trainingsset verwendet werden. 

### Variante: stratifizierte Kreuzvalidierung 
- Bei der stratifizierten Kreuzvalidierung wird sicherstellen, dass die Klassenverteilung in jedem Fold ähnlich der gesamten Klassenverteilung im Datensatz ist. Das bedeutet, dass jeder Fold eine proportional ähnliche Anzahl von Beispielen jeder Klasse enthält. 

### Variante: Nested Cross-Validation 
- eine Technik zur Modellbewertung und Hyperparameteroptimierung, bei der zwei verschachtelten Schleifen der Kreuzvalidierung verwendet werden: eine äußere Schleife zur Bewertung des Modells und eine innere Schleife zur Auswahl und Optimierung der Hyperparameter. 


# Verbesserungen 
- Modellauswahl und Hyperparameter-Optimierung 
- Feature-Engineering 
- Kontrolle über die Regularisierung 

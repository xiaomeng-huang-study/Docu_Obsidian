# ML Verfahren 
## 1. Decision-Tree 

## 2. Sigmoid-Funktion 
- Formulierung: $\sigma(z) = \frac{1}{1+e^{-z}}$ 
- Anwendung 
	- in NN: Aktivierungsfunktion, um die nichtlinearen Zusammenhänge zu erlernen. 
	- in Logistische Regression: stetige Werte in Wahrscheinlichkeiten zwischen 0 und 1 umzuwandeln, was hilfreich ist, binäre Entscheidungen zu treffen. 

## 3. k-Means Verfahren 

## 4. Underfitting und Overfitting 
- Underfitting: Modell zu einfach, um die zugrunde liegenden Muster der Trainingsdaten zu erfassen 
- Overfitting: Modell zu komplex ist und sich zu sehr an die Trainingsdaten anpasst. 
- Visualisierung: [[Notiz_Underfitting_Overfitting#Underfitting_Overfitting|Underfitting und Overfitting]] 


# Bewertung 
## 3. Stratified Cross Validation 
- eine Technik der Kreuzvalidierung, bei der die Daten so in K-Falten aufgeteilt werden, dass jede Falte die gleiche proportionale Verteilung der Klassenlabels (Zielvariablen) wie der gesamte Datensatz aufweist. 
# Methoden für Klassifikation und Regression 
- [[#KNN|k-Nearest Neighbors (KNN)]] 
- [[#Decision Trees]] 
- [[#Random Forest]] 


## KNN 
- Ein nicht-parametrischer Algorithmus, der eine neue Beobachtung anhand der **Mehrheit** der Klassen der k nächsten Nachbarn klassifiziert oder den **Mittelwert** der k nächsten Nachbarn zur Regression verwendet. 
### Arbeitsverlauf 
1. Berechnung der Distanz nach 
	- Minkowski Distanz $d(p, q)=\left(\sum_{i=1}^{n}\left|p_{i}-q_{i}\right|^{r}\right)^{\frac{1}{r}}$ 
		- $r = 2$: Euklidische Distanz $d(p, q)=\sqrt{\sum_{i=1}^{n}\left(p_{i}-q_{i}\right)^{2}}$ 
		- $r = 1$: Manhattan Distanz $d(p, q)=\sum_{i=1}^{n}\left|p_{i}-q_{i}\right|$ 
	- Hamming Distanz $d(p, q)=\sum_{i=1}^{n} \delta\left(p_{i} \neq q_{i}\right)$ $\text { wobei } \delta \text { eine Funktion ist, die } 1 \text { zurückgibt, wenn } p_{i} \neq q_{i} \text {, und } 0 \text { sonst. }$ 
2. Bestimmung der $k$ nächsten Nachbarn 
3. Für Klassifikation: Mehrheitsabstimmung 
	- <img src="https://github.com/xiaomeng-huang-study/images_DAAN/blob/main/Scrennshot_2024-07-06_19-20-50.png?raw=" width="70%" /> 
3. Für Regression: Mittelwert 


## Decision Trees 
- Ein baumbasierter Algorithmus, der Entscheidungen auf Basis von **Merkmalswerten** trifft, um den Zielwert zu bestimmen. 
### Maß für die Unreinheit
- Entropie 
	- $I_H(D) =-\sum_{i=0}^{\kappa-1}p(i\vert D)\log_2 p(i\vert D)$ 
- Gini-Index ^GI
	- $\begin{array}{ll}I_G(D) &=\sum_{i=0}^{\kappa-1}p(i\vert D)(1-p(i\vert D))\\ &= 1 - \sum_{i=0}^{\kappa-1}p(i\vert D)^2\\ \end{array}$ 
	- kleinere GI $\rightarrow$ Knoten homogener 
### Arbeitsverlauf 
1. Berechne die [[#^GI|GI]] eines jeden Kindknotens bei einem möglichen Split 
2. Berechne die $Gini_\text{split}$ eines jeden Splits als den gewichteten mittleren GI der Kindknoten $Gini_\text{split} = \frac{n_l}{n_p}I_{G} (D_l) + \frac{n_r}{n_p}I_{G} (D_r)$ 
3. Wähle den Split mit dem kleinsten $Gini_\text{split}$ 
4. (Wiederholung bis kein Split mehr möglich) 
- Beispiel 
	- <img src="https://github.com/xiaomeng-huang-study/images_DAAN/blob/main/Scrennshot_2024-07-07_23-20-00.png?raw=" width="80%" /> 
	- <img src="https://github.com/xiaomeng-huang-study/images_DAAN/blob/main/Scrennshot_2024-07-06_18-56-06.png?raw=" width="40%" /> 

## Random Forest 
- Eine Ensemble-Methode, die aus **mehreren Entscheidungsbäumen** besteht, die zufällig ausgewählten Teilmengen der Trainingsdaten trainiert werden. Die endgültige Vorhersage ergibt sich aus Mehrheitsbestimmung / Mittelwert der Bäume. 
- <img src="https://github.com/xiaomeng-huang-study/images_DAAN/blob/main/Scrennshot_2024-07-06_22-07-15.png?raw=" width="90%" /> 


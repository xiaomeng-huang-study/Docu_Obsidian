# Klassifikation 
## Algorithmen 
- [[#Decision Trees]] 
- [[#KNN (K-Nearest Neighbors)|KNN]] 


## Algorithmen 
### Decision Trees 
#### Maß für die Unreinheit
- Entropie 
- Gini-Index ^GI
	- $\begin{array}{ll}I_G(D) &=-\sum_{i=0}^{\kappa-1}p(i\vert D)(1-p(i\vert D))\\ &= 1 - \sum_{i=0}^{\kappa-1}p(i\vert D)^2\\ \end{array}$ 
	- kleinere GI $\rightarrow$ Knoten homogener 
#### Arbeitsverlauf 
1. Berechne die [[#^GI|GI]] eines jeden Kindknotens bei einem möglichen Split 
2. Berechne die GI-Impurity eines jeden Splits als den gewichteten mittleren GI der Kindknoten $G(D_p,f) = I(D_p) - \frac{n_l}{n_p}I(D_l) - \frac{n_r}{n_p}I(D_r)$ 
3. Wähle den Split mit dem kleinsten GI-Impurity 
4. (Wiederholung bis kein Split mehr möglich) 
- Beispiel 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-06_18-54-00.png?raw=" width="90%" /> 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-06_18-56-06.png?raw=" width="40%" /> 

---
### KNN (K-Nearest Neighbors) 
#### Arbeitsverlauf 
1. Berechnung der Distanz nach 
	- Minkowski Distanz $d(p, q)=\left(\sum_{i=1}^{n}\left|p_{i}-q_{i}\right|^{r}\right)^{\frac{1}{r}}$ 
		- $r = 2$: Euklidische Distanz $d(p, q)=\sqrt{\sum_{i=1}^{n}\left(p_{i}-q_{i}\right)^{2}}$ 
		- $r = 1$: Manhattan Distanz $d(p, q)=\sum_{i=1}^{n}\left|p_{i}-q_{i}\right|$ 
	- Hamming Distanz $d(p, q)=\sum_{i=1}^{n} \delta\left(p_{i} \neq q_{i}\right)$ $\text { wobei } \delta \text { eine Funktion ist, die } 1 \text { zurückgibt, wenn } p_{i} \neq q_{i} \text {, und } 0 \text { sonst. }$ 
2. Bestimmung der $k$ nächsten Nachbarn 
3. Mehrheitsabstimmung 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-06_19-20-50.png?raw=" width="70%" /> 

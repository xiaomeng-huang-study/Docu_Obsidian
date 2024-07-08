# Clustering 
## Algorithmen 
- [[#K-means]] 
- [[#Hierarchisches / Agglomerative Clustering]] 
- [[#Density-based spatial clustering of applications with noise(DBSCAN) [Video](https //youtu.be/6jl9KkmgDIw?si=g_vKcXEFBlpRVAIg)|DBSCAN]] 
## Bewertung 
- [[#Silhouetten-Koeffizient]] 
- [[#Davies-Bouldin-Index ]] 

## Algorithmen 
### K-means 
- eine Menge von Datenpunkten in k verschiedene Gruppen (Cluster) zu unterteilen 
#### Arbeitsverlauf 
1. wähle zufällige **[[#Bestimmung der optimalen Anzahl n |n]]** Cluster-Center aus 
2. weise Datenpunkte dem nächstgelegenen Center zu 
3. verschiebe Zentren in die Mitte der zugehörigen Datenpunkte 
4. (Wiederholung von 2. - 3. bis keine neue Zuordnung erfolgt) 
- Pseudo-Code 
	```pseudo
	1. Initialisiere k Zentroiden zufällig aus den Datenpunkten.
	2. Wiederhole bis zur Konvergenz:
	    a. Weise jeden Datenpunkt dem nächstgelegenen Zentroiden zu.
	    b. Berechne die neuen Zentroiden als Mittelwert der Datenpunkte in jedem Cluster.
	```
- Visualisierung 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_19-23-00.png?raw=" width="90%" /> 
- Code-Beispiel 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_20-17-24.png?raw=" width="90%" /> 

#### Bestimmung der optimalen Anzahl n 
Methoden 
- [[#Elbow method]] 
- Silhouette-method 

##### Elbow method 
- Bewertung der Qualität: anhand der maximalen Distanz von Cluster-Punkten eines Clusters über alle Cluster (Diameter) 
	- Visualisierung 
		- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_19-43-13.png?raw=" width="50%" /> 
- Auswahl des "Ellbogens": Stelle des merklichen Abflachens der Kurve 
	- Visualisierung 
		- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_19-40-44.png?raw=" width="30%" /> 

---
### Hierarchisches / Agglomerative Clustering 
#### Arbeitsverlauf 
1. Initialisierung: Jeder Datenpunkt bildet ein eigenes Cluster. 
2. Berechnung der Abstände: zwischen allen Paaren von Clustern nach der Distanzmaße 
	- euklidischer Abstand 
	- Manhattan-Distanz 
	- Cosinus-Ähnlichkeit 
3. Zusammenführung der nächstgelegenen Cluster: Fusionierung der 2 Clustern mit dem kleinsten Abstand 
4. Aktualisierung der Abstände 
	- Single Linkage (Minimum Linkage) 
	- Complete Linkage (Maximum Linkage) 
	- Average Linkage 
	- Ward's Method 
5. (Wiederholung von 3. und 4. bis angeforderte Anzahl der Clusters erreicht wird) 
- Pseudo-Code
	```pseudo
	1. Weise jedem Datenpunkt ein eigenes Cluster zu 
	2. Bestimme die Abstände der Clusters nach Metriken 
		1. "Euklidischer Abstand" 
		2. "Manhattan-Distanz" 
		3. Cosinus-Ähnlichkeit 
	3. Wiederhole bis die Anzahl der Clusters kleiner als die angeforderten Anzahl: 
		a. Fusionierung der 2 Clusters mit dem kleinsten Abstand 
		b. Berechnung der Distanz nach 
			- "Single-Linkage" 
			- "Complete-Linkage" 
			- Average-Linkage 
			- Ward's method 
	```
- Hyperparameter 
	- `n_clusters` 
	- `metric` 
	- `linkage` 
- Visualisierung mit Dendrogram 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_20-37-00.png?raw=" width="90%" /> 
- Code-Beispiel 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_20-18-18.png?raw=" width="70%" /> 

#### Bestimmung der Anzahl der Clusters 
<img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_20-44-52.png?raw=" width="50%" /> 
- Welche Distanz wird genommen (je höher, weniger Clusters) 
- oder Anzahl der Clusters 

---
### Density-based spatial clustering of applications with noise(DBSCAN) [Video](https://youtu.be/6jl9KkmgDIw?si=g_vKcXEFBlpRVAIg) 
#### Konzepte 
- $\epsilon$ : Radius 
- $MinPts$ 
#### Arbeitsverlauf 
1. Klassifizierung der Punkte 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_22-28-00.png?raw=" width="90%" /> 
	- Core-Points: hat min. $MinPts$ Nachbarn im Radius $\epsilon$ 
	- Border-Points: weniger als $MinPts$ Nachbarn im Radius $\epsilon$, aber im $\epsilon$-Bereich eines Core-Points 
	- Outlier-Points: weder Core-Points, noch Border-Points 
2. Cluster 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_22-32-18.png?raw=" width="30%" /> 
- Code-Beispiel 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_23-04-31.png?raw=" width="70%" /> 

## Bewertung 
### Silhouetten-Koeffizient 
- misst, wie ähnlich ein Punkt zu seinem eigenen Cluster im Vergleich zu anderen Clustern ist. 
$$
s^{(i)} := \frac{b^{(i)} - a^{(i)}}{\text{max}\{b^{(i)},a^{(i)}\}}\quad\in[-1,1]
$$
- *Separation / Trennung* $b^{(i)}$: durchschnittlicher Abstand eines Datenpunktes $\mathbf{x}^{(i)}$ zu allen Datenpunkten im nächstgelegenen Cluster, zu dem $\mathbf{x}^{(i)}$ **nicht** gehört (Unähnlichkeit zu anderen Clustern) 
- *Cohesion / Kohäsion* $a^{(i)}$: durchschnittlicher Abstand eines Datenpunktes $\mathbf{x}^{(i)}$ zu allen anderen Datenpunkten des Clusters (Ähnlichkeit innerhalb des Clusters) 
- *Silhouette* als gewichtete Differenz von Cohesion und Separation $s^{(i)}$ 
- Idealerweise, $b^{(i)}>>a^{(i)} \Rightarrow s^{(i)}\approx 1$ 
### Davies-Bouldin-Index 
- Der Davies-Bouldin-Index bewertet die Clusterqualität, indem er das Verhältnis der durchschnittlichen Intra-Cluster-Distanzen (Cluster-Durchmesser) zur Inter-Cluster-Distanz (Abstand zwischen den Cluster-Zentroiden) misst. 
- $[0, ~\infty]$ 
- niedrigerer Wert $\rightarrow$ bessere Qualität 
### Visualisierung 
- Cluster-Einfärbung 
- Scatterplots 
<img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_22-50-06.png?raw=" width="90%" /> 

# Einteilung 
- Unsupervised Learning 
	- Strukturen, Gruppen erkennen 
	- Vorhersagegüte / Qualität nur über bekannte Daten 
	- **Methoden** : [[#Clustering]], Assoziationsanalyse, Dimensionsreduktion 
- Supervised Learning 
	- Zusammenhänge lernen $\Rightarrow$ Vorhersagen 
	- Vorhersagen bei vorhandenen historischen Daten 
	- **Methoden** : Regression, Klassifikation, Entscheidungsbäume 

# Clustering 
Algorithmen
- [[#K-means]] 
- [[#Hierarchisches / Agglomeratives Clustering]] 

### K-means 
#### Arbeitsverlauf 
1. wähle zufällige **[[#Bestimmung der optimalen Anzahl n |n]]** Cluster-Center aus 
2. weise Datenpunkte dem nächstgelegenen Center zu 
3. verschiebe Zentren in die Mitte der zugehörigen Datenpunkte 
4. (Wiederholung von 1. bis keine neue Zuordnung erfolgt) 
- Visualisierung 
	- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_19-23-00.png?raw=" width="500" /> 

#### Bestimmung der optimalen Anzahl n 
Methoden 
- [[#Elbow method]] 
- Silhouette-method 

##### Elbow method 
- Bewertung der Qualität: anhand der maximalen Distanz von Cluster-Punkten eines Clusters über alle Cluster (Diameter) 
	- Visualisierung 
		- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_19-43-13.png?raw=" width="400" /> 
- Auswahl des "Ellbogens": Stelle des merklichen Abflachens der Kurve 
	- Visualisierung 
		- <img src="https://github.com/ICH-BIN-HXM/images_DAAN/blob/main/Scrennshot_2024-07-04_19-40-44.png?raw=" width="200" /> 

---
### Hierarchisches / Agglomeratives Clustering 

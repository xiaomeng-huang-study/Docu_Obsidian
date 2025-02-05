# geometrische Merkmale 
- Surface curvatures 
	- Die Kurvatur beschreibt, wie stark die Oberfläche um einen Punkt gekrümmt ist. 
- Surface normals 
	- Der Normalenvektor eines Punktes zeigt die Orientierung der Oberfläche um diesen Punkt. 
- Bestimmung 
	- Schwerpunkt aller Nachbarpunkte $p_{i}$ 
		- $\bar{p}=\frac{1}{k} \sum_{i=1}^{k} p_{i}$ 
	- $3 \times 3$ Covariance matrix: 
		- $C=\frac{1}{k} \sum_{i=1}^{k} \alpha_{i}\left(p_{i}-\bar{p}\right)\left(p_{i}-\bar{p}\right)^{t}$ 
	- Eigenvektoren mit PCA berechnen 
		- $C \cdot \overrightarrow{v_{j}}=\lambda_{j} \cdot \overrightarrow{v_{j}}, \quad j \in\{0,1,2\}$ 
	- kleinster Eigenwert $\rightarrow$ Normalenvektor $+\vec{n}, -\vec{n}$ 
	- Surface curvature $\sigma_{p}=\frac{\lambda_{0}}{\lambda_{0}+\lambda_{1}+\lambda_{2}}$ 


# k-Nachbarschaft 
- Definition 
	- Die $k$-Nachbarschaft eines 3D-Punktes in einer Punktwolke bezeichnet die $k$ nächstgelegenen Punkte (Nachbarn) zu diesem Punkt basierend auf ihrer räumlichen Distanz. 
- Auffindung 
	- Brute-Force-Methode 
		- Berechnung der Distanz zu allen Punkten, Sortierung und Auswahl der $k$ Punkten mit kleinsten Distanzen. 
	- Effizientere Ansätze 
		- kd-Tree 
		- Octree 
	- Radius-basierte Nachbarschaft 
		- alle Punkte innerhalb Distanz $r$ werden als Nachbarn betrachtet. 
- Reduzierung des Suchaufwands 
	- Aus der Perspektive der methodischen Verbesserung: Brute-Force ($n^2$) $\rightarrow$ kd-Tree ($nlog{n}$) 
	- Aus der Perspektive der technologischen Verbesserungen: mit `OpenMP` Algorithmus zu parallelisieren 


# Problem bei der Normalen 
- Rauschen 
- Ungleichmäßige Punktdichte 
- Unklarheit der Ausrichtung von Normalenvektoren 
	- Lösung: Richtungsvektor zur Kamera berechnen, Normalenvektor ggf. invertieren 


# geometrische Unterteilungsfunktionen 
- Octree: eine hierarchische Baumstruktur, die den 3D-Raum rekursiv in acht gleich große Räume unterteilt 
- k-d-Tree: eine binäre Baumstruktur, die den Raum rekursiv entlang einer der $k$-dimensionalen Achsen unterteilt (für 3D-Punkte also entlang der x-, y- und z-Achse). 
- Box Decomposition Tree (BD-Tree): eine spezielle Form des k-d-Trees und ähnelt dem k-d-Tree, jedoch mit dem Unterschied, dass er den Raum durch axis-aligned Boxen (Achsen ausgerichtete Boxen) unterteilt. 


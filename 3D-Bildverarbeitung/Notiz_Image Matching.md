- Ziel: wichtige Bildeigenschaften auf den Bildern mittels geeigneten Operatoren zu detektieren. Die detektierten Merkmalspunkte (feature points) in den Bildern werden zugeordnet, somit die Transformationsparameter zur Bildausrichtung berechnet werden können. 

# SIFT-Operator 
- Scale-Invariant Feature Transform 
- Dies gelingt durch einen kaskadierenden Ansatz, der das Bild in verschiedenen Auflösungen betrachtet (SIFT-Detektor DoG) und die dominanten Gradientenrichtungen mittels lokalen Gradientenhistogrammen detektiert (SIFT-Deskriptor). 
- Woraus besteht der Keypoint-Deskriptor? 
	- ein Vektor, der alle Merkmale zu diesem Keypoint beinhaltet. Der Vektor hat eine Dimension von 4 × 4 × 8 = 128, somit 128 Merkmale. 
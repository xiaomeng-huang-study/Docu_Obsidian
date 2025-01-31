- Ziel: wichtige Bildeigenschaften auf den Bildern mittels geeigneten Operatoren zu detektieren. Die detektierten Merkmalspunkte (feature points) in den Bildern werden zugeordnet, somit die Transformationsparameter zur Bildausrichtung berechnet werden können. 

# SIFT-Operator 
- Scale-Invariant Feature Transform 
- Dies gelingt durch einen kaskadierenden Ansatz, der das Bild in verschiedenen Auflösungen betrachtet (SIFT-Detektor DoG) und die dominanten Gradientenrichtungen mittels lokalen Gradientenhistogrammen detektiert (SIFT-Deskriptor). 
- Merkmale 
	- Rotationsinvarianz 
		- Wird durch die Zuweisung einer Hauptrichtung an Keypoints erreicht. Anhand des Gradientenrichtungenshistogramms wird die dominante Richtung ermittelt. 
	- Skalierungsinvarianz 
		- Der Algorithmus baut einen Skalenraum, indem das Bild mit Gaussfiltern unterschiedlicher Stärken bearbeitet und untergesampelt wird. 
	- Beleuchtungsinvarianz 
		- SIFT basiert auf Gradienteninformation, die die relative Intensitätsänderung widerspiegelt und nicht von absoluten Helligkeitswerten abhängt. 


# Kantendetektoren 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-31_17-51-54.png?raw=" width="80%" /> 
- zwei Klassen von Kantenfiltern 
	- basierend auf der ersten Ableitung und der Analyse des Gradienten 
	- basierend auf der zweiten Ableitung und der Analyse der Nulldurchgänge 


# Eckpunkt-Detektor 

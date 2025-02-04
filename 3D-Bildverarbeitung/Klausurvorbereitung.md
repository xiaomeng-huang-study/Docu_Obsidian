# Offene Fragen 
## Beschreiben Sie die Algorithmen-Pipeline zur Erstellung eines 3D-Modells aus mehreren Punktwolken 
- In Echtzeit 
	- Kinect Fusion 
	- SLAM 
- Nicht in Echtzeit 
	- SfM 

## Wie wurden die Punktwolken aufgeräumt und warum wurde dieser Weg gewählt? 
- Effizienz 
	- Downsampling 
- Genauigkeit 
	- Normalen (Oberflächenorientierungen) 
- Qualität 
	- Entfernen von Rauschen 

## Wie wurden die Keypoints gewählt? 
- SIFT 
- Kanten-Detektion 
	- 1. Ableitung 
	- 2. Ableitung 
- Eckpunkte-Detektion 
	- Harris-Corner-Detector 
	- Hessian-Corner-Detector 
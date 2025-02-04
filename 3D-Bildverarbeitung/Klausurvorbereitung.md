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

## Wie funktioniert der Voxelgrid Filter und wann wird er eingesetzt? Was ist beim Voxelgrid Filter die Leafsize und in welcher Einheit wird diese angegeben? 

## 2D Transformationen 

## Wie kann eine Kamerabewegung verfolgt werden? 
(Prinzip als Referenz) 
- In Echtzeit 
	- Kinect Fusion 
	- SLAM 
- Nicht in Echtzeit 
	- SfM 
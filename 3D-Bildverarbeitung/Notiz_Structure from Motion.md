# Definition 
- aus einer Reihe von 2D-Bildern die dreidimensionale Struktur einer Szene sowie die Kamerapositionen zu rekonstruieren. 


# Eingaben 
- Eine Reihe von 2D-Bildern derselben Szene, die aus verschiedenen Blickwinkeln und Positionen aufgenommen wurden. 


# Ausgaben 
- Eine Menge von 3D-Punkten, die die rekonstruierte Struktur der Szene darstellen. 
- Die Position (X, Y, Z) und Orientierung (Rotation) der Kamera für jedes aufgenommene Bild relativ zur rekonstruierten Szene. 


# Prozess 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-13_09-11-43.png?raw=" width="90%" /> 
- 1. Merkmalserkennung (Feature Detection) 
- 2. Merkmalszuordnung (Feature Matching) 
- 3. Schätzung der Kamerapositionen und der 3D-Struktur 
	- Fundamentalmatrix oder Essential Matrix: Wird aus den Korrespondenzen berechnet, um die relative Position und Orientierung zwischen zwei Kameras zu schätzen. 
	- Triangulation: Die 3D-Positionen der korrespondierenden Merkmale werden aus den Kamerapositionen und den Bildkoordinaten berechnet. 
- 4. Bundle Adjustment: Verfeinerung der 3D-Struktur und der Kamerapositionen, um Fehler zu minimieren. 


# Photo Connectivity Graph 
- ein Graph, bei dem: 
	- Knoten: Die einzelnen Bilder (Views) der Szene repräsentieren. 
	- Kanten: Die Verbindungen zwischen den Bildern darstellen, wenn sie gemeinsame Merkmale (Feature Matches) aufweisen. 


# Fragen 
- Projektive Transformation basierend auf dem Pinhole-Kameramodell 
- 11 Freiheitsgrade 
- 
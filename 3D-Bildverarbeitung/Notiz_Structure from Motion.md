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


# Limitierungen 
- Wenn die Bilder keine ausreichenden gemeinsamen Merkmale aufweisen, kann der Algorithmus keine zuverlässigen Korrespondenzen finden. 
	- Fehlende Überlappung 
	- Schlechte Bildqualität 
- SfM hat Schwierigkeiten, mit sehr großen Datensätzen (z. B. Tausenden von Bildern) umzugehen, da die Komplexität der Berechnungen stark ansteigt. 
	- Rechenzeit 
	- Speicherbedarf 
- Wenn die Szene hauptsächlich aus flachen Oberflächen besteht (z. B. eine Wand oder ein Tisch), fehlt diese Parallaxe. 
	- Fehlende Tiefeninformation 


# Wofür wird die SVD hier verwendet? 
- Schätzung der Fundamentalmatrix oder Essenziellen Matrix 
- Triangulation von 3D-Punkten 
- Bundle Adjustment 


# Texturbilddaten 
- Definition 
	- Texturbilddaten sind 2D-Bilder (Texturen), die auf die Oberfläche eines 3D-Modells projiziert werden, um dessen visuelles Erscheinungsbild zu verbessern. 
- Inhalte 
	- Farben (z. B. die Farbe einer Wand oder eines Objekts) 
	- Muster (z. B. die Struktur von Holz, Stein oder Stoff) 


# Fragen 
## Welche Transformation wird dazu angenommen und wie viele Freiheitsgrade hat diese? 
- Projektive Transformation basierend auf dem Pinhole-Kameramodell 
- 11 Freiheitsgrade 

## Ist SfM echzeitfähig? Komplexität und Performanz 
- Merkmalserkennung und -zuordnung 
	- $O(N^2)$ 
- Kameraschätzung 
- Triangulation 
- Bundle Adjustment 
	- $O\left(n \cdot m^{2}\right)$, wobei $n$ die Anzahl der 3D-Punkte und $m$ die Anzahl der Kameras ist. 
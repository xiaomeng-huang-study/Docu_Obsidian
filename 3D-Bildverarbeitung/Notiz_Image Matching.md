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
## Hessian-Corner-Detector 
- Hessische Matrix 
	- $\mathbf{H}=\left(\begin{array}{ll}H_{11} & H_{12} \\H_{21} & H_{22}\end{array}\right)=\left(\begin{array}{cc}I_{x x} & I_{x y} \\I_{y x} & I_{y y}\end{array}\right)$ 
	- wobei $I_{xy}$ die diskrete Ableitung des Bildes $I$ erst in $x-$ und dann in $y-$Richtung bedeutet. $I_{xx}$ ist die 2.te Ableitung in $x-$Richtung. 
- Der Betrag der Determinanten der Hessischen Matrix 
	- $\|\operatorname{det}(\mathbf{H})\|=\left\|H_{11} H_{22}-H_{12} H_{21}\right\|=\left\|I_{x x} I_{y y}-I_{x y}^{2}\right\|$ 
- Eigenwerte 
	- $\operatorname{det}(H-\lambda I)=0$ $\Rightarrow$ $\lambda_1, \lambda_2$ 
	- beschreiben die Stärke der Krümmung in den Hauptachsenrichtungen der lokalen Bildstruktur. 
	- $\lambda_{1} \approx 0$ und $\lambda_{2} \approx 0$ : Flache Region 
	- $\lambda_{1} \gg 0$ und $\lambda_{2} \approx 0$ : Kante 
	- $\lambda_{1} \gg 0$ und $\lambda_{2} \gg 0$ : Ecke 

## Harris Corner Detector 
- Corner Response Function 
	- $R=\operatorname{det}(H)-k \cdot \operatorname{trace}(H)^{2}$ 
		- wobei $\operatorname{det}(H)=I_{x x} \cdot I_{y y}-I_{x y}^{2}$, $\operatorname{trace}(H)=I_{x x}+I_{y y}$, $k$ ein empirischer Parameter. 
	- $R > 0$ : Ecke 
	- $R \approx 0$ : Kante 
	- $R < 0$ : Flache Region 

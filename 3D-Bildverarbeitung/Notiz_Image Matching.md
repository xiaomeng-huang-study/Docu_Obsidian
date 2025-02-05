- Ziel: wichtige Bildeigenschaften auf den Bildern mittels geeigneten Operatoren zu detektieren und zuordnen, somit die Transformationsparameter zur Bildausrichtung berechnet werden können. 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-08_22-24-56.png?raw=" width="90%" /> 


# Image Stitching 
## 1. Keypoint Detection (Localization) 
- Keypoint (feature point / interesting point) 
	- charakteristische Punkte in einem Bild, die eindeutig und konsistent in verschiedenen Ansichten oder unter verschiedenen Beleuchtungsbedingungen erkannt werden können. 
	- z.B. Ecken, Kanten, Blob, Textur- oder Musterbereiche 
- Methoden 
	- [[Notiz_Image Matching#SIFT Detector SIFT-Detector|SIFT-Detector]] 
	- [[Notiz_Image Matching#Harris Corner Detector Harris-Corner-Detector|Haris Corner Detector]] 
	- [[Notiz_Image Matching#Hessian Detector Hessian-Detector|Hessian Detector]] 

## 2. Keypoint Description 
- Keypoint descriptor 
	- save the neighborhood informations around a keypoint as a description of the object, usually as feature vectors 
- Methoden 
	- [[Notiz_Image Matching#SIFT Descriptor SIFT-Descriptor|SIFT Descriptor]] 

## 3. Descriptor matching 
- Matching 
	- Calculate the distances between the feature vectors 
	- search similar keypoint descriptors 
	- and use the most similar feature vectors as corresponding points 


# SIFT-Operator 
## Definition 
- SIFT: Scale-Invariant Feature Transform 

## SIFT Detector^SIFT-Detector
### Step 1: Gaussian and Difference-of-Gaussian pyramid 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_18-03-31.png?raw=" width="60%" /> 

- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_21-25-47.png?raw=" width="60%" /> 
- scale: Grad der Unschärfe. Ein größerer "scale" entspricht einer größeren Entfernung beim Betrachten, wodurch das Bild unschärfer und kleiner wird. 
- octave: Jede "octave" besteht aus einer Gruppe von Bildern, die die gleiche Größe haben, aber unterschiedliche Unschärfe (verschiedene "scales") aufweisen. 

### Step 2: Detect Minima and Maxima 
<img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_21-44-43.png?raw=" width="40%" /> 
- A point is selected as keypoint if it is higher or lower than all 26 (3 x 3 x 3 - 1) neighbors. 
- $\sigma$ : the smaller of the two gaussian images from the DoG image 

### Step3: Select Keypoints 
- Keypoints mit geringem Kontrast werden eliminiert 

### Step4: Eliminate false edges 
- Anpassung an grundlegende Kurven 

## SIFT Descriptor^SIFT-Descriptor
- ein Vektor, der alle Merkmale zu diesem Keypoint beinhaltet. Der Vektor hat eine Dimension von 4 × 4 × 8 = 128, somit 128 Merkmale. 

### Step 1: Detect Keypoint orientation 
- Calculate in a preprocessing step all gradient magnitudes and orientations to all gaussian images L 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_22-10-06.png?raw=" width="60%" /> 
- Weight the orientation 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_22-05-59.png?raw=" width="20%" /> 
- Histogram of Oriented Gradients (HOG) 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_22-07-14.png?raw=" width="90%" /> 
	- (36 bins x 10°/bin = 360°) 
	- 1. Richtungsquantisierung: die Gradientenrichtung jedes Pixels wird in diskrete Richtungsintervalle 10°/bin quantisiert 
	- 2. die Häufigkeit, mit der jede Richtung des Gradienten in dieser Zelle auftritt, wird für jedes bin berechnet 
	- 3. Hauptrichtung auswählen 

### Step 2: Description 
- Define a squared 16x16 region around the keypoint, divide the region into 16 equal blocks by 4x4 pixel 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_22-15-22.png?raw=" width="30%" /> 
- Rotate the region according to the keypoint orientation 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_22-22-03.png?raw=" width="80%" /> 
- 16 blocks x 8 directions/block = 128 directions $\Rightarrow$ SIFT Descriptor $\left(\begin{array}{c}m_{1} \\\vdots \\m_{128}\end{array}\right)$ 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_22-24-00.png?raw=" width="30%" /> 

## Merkmalen 
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
## Harris Corner Detector 
- Second Moment Matrix 
	- $M=\left(\begin{array}{cc}F\left(I_{x}^{2}\right) & F\left(I_{x} I_{y}\right) \\F\left(I_{y} I_{x}\right) & F\left(I_{y}^{2}\right)\end{array}\right)$ 
		- wobei $F$ Gauß-Filter ist, $F\left(I_{x}^{2}\right)$ $F\left(I_{y}^{2}\right)$ Quadrat der Ableitungen in $x$ und $y$ Richtungen sind, $F\left(I_{x} I_{y}\right)$ $F\left(I_{y} I_{x}\right)$ Summe der Produkte sind. 
- Eigenwerte  
	- $\operatorname{det}(M-\lambda I)=0$ $\Rightarrow$ $\lambda_1, \lambda_2$ 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_12-49-38.png?raw=" width="30%" /> 
	- beschreiben die **Stärke der Krümmung** in den Hauptachsenrichtungen der lokalen Bildstruktur. 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_12-53-58.png?raw=" width="50%" /> 
	- $\lambda_{1} \approx 0$ und $\lambda_{2} \approx 0$ : Flache Region 
	- $\lambda_{1} \gg 0$ und $\lambda_{2} \approx 0$ : Kante 
	- $\lambda_{1} \gg 0$ und $\lambda_{2} \gg 0$ : Ecke 
- Corner Response Function 
	- - <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_12-57-22.png?raw=" width="50%" /> 
	- $\begin{array}{l}R &=\operatorname{det}(M)-k \cdot \operatorname{trace}(M)^{2} \\&=\lambda_{1} \lambda_{2}-k \cdot\left(\lambda_{1}+\lambda_{2}\right)^{2}\end{array}$ 
		- wobei $k$ ein empirischer Parameter ist. 
	- $R > 0$ : Ecke 
	- $R \approx 0$ : Kante 
	- $R < 0$ : Flache Region 

## Hessian-Corner-Detector 
- Hessische Matrix 
	- $H=\left(\begin{array}{ll}H_{11} & H_{12} \\H_{21} & H_{22}\end{array}\right)=\left(\begin{array}{cc}I_{x x} & I_{x y} \\I_{y x} & I_{y y}\end{array}\right)$ 
	- wobei $I_{xy}$ die diskrete Ableitung des Bildes $I$ erst in $x-$ und dann in $y-$Richtung bedeutet. $I_{xx}$ ist die 2.te Ableitung in $x-$Richtung. 
- Der Betrag der Determinanten der Hessischen Matrix 
	- $\|\operatorname{det}(H)\|=\left\|H_{11} H_{22}-H_{12} H_{21}\right\|=\left\|I_{x x} I_{y y}-I_{x y}^{2}\right\|$ 
- Eigenwerte 
	- $\operatorname{det}(H-\lambda I)=0$ $\Rightarrow$ $\lambda_1, \lambda_2$ 
	- beschreiben die **Stärke der Krümmung** in den Hauptachsenrichtungen der lokalen Bildstruktur. 
	- $\lambda_{1} \approx 0$ und $\lambda_{2} \approx 0$ : Flache Region 
	- $\lambda_{1} \gg 0$ und $\lambda_{2} \approx 0$ : Kante 
	- $\lambda_{1} \gg 0$ und $\lambda_{2} \gg 0$ : Ecke 
- Corner Response Function 
	- $R=\operatorname{det}(H)-k \cdot \operatorname{trace}(H)^{2}$ 
		- wobei $\operatorname{det}(H)=I_{x x} \cdot I_{y y}-I_{x y}^{2}$, $\operatorname{trace}(H)=I_{x x}+I_{y y}$, $k$ ein empirischer Parameter. 
	- $R > 0$ : Ecke 
	- $R \approx 0$ : Kante 
	- $R < 0$ : Flache Region 


# Invarianz gegenüber Transformationen 
| Eigenschaft               | Hessian & Harris Corner Detector | SIFT                        |
| ------------------------- | -------------------------------- | --------------------------- |
| Rotation                  | Invariant                        | Invariant                   |
| Skalierung                | Nicht invariant                  | Invariant                   |
| Translation               | Invariant                        | Invariant                   |
| Beleuchtungsänderung      | Teilweise invariant              | Invariant                   |
| Affine Transformation     | Teilweise invariant              | Robust (aber nicht perfekt) |
| Nichtlineare Verzerrungen | Nicht invariant                  | Nicht invariant             |
- Rotation 
	- Hessian & Harris Corner Detector basiert auf Gradienten und reagieren daher nicht auf Rotation 
		- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_13-04-05.png?raw=" width="30%" /> 
	- SIFT ist zusätzlich darauf optimiert, lokale Keypoints eine Orientierung zuzuweisen, was eine explizite Rotationsinvarianz gewährleistet. 
- Skalierung 
	- Hessian & Harris Corner Detector ist nicht skaleninvariant. Aufgrund der Skalierung ist es möglich, dass ein Bereich, der ursprünglich als Ecke erkannt wurde, nun als Kante erkannt wird. 
		- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_13-05-35.png?raw=" width="50%" /> 
	- SIFT verwendet eine Gaussian Scale-Space-Repräsentation, wodurch Keypoints über mehrere Skalen hinweg erkannt werden können. 
- Translation: Alle Methoden sind translational invariant, da lokale Merkmale (Gradienten oder Ableitungen) unabhängig von der absoluten Position im Bild berechnet werden. 
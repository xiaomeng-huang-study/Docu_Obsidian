<img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-08_22-24-56.png?raw=" width="90%" /> 

# Image Stitching 
## 1. Keypoint Detection (Localization) 
- Keypoint (feature point / interesting point) 
	- charakteristische Punkte in einem Bild, die eindeutig und konsistent in verschiedenen Ansichten oder unter verschiedenen Beleuchtungsbedingungen erkannt werden können. 
	- z.B. Ecken, Kanten, Blob, Textur- oder Musterbereiche 
- Methoden 
	- [[Notiz_Keypoints and Descriptors#SIFT detector SIFT-Detector|SIFT Detector]] 
	- [[Notiz_Keypoints and Descriptors#Harris Corner Detector Harris-Corner-Detector|Haris Corner Detector]] 
	- [[Notiz_Keypoints and Descriptors#Hessian Detector Hessian-Detector|Hessian Detector]] 
## 2. Keypoint Description 
- Keypoint descriptor 
	- save the neighborhood informations around a keypoint as a description of the object, usually as feature vectors 
- Methoden 
	- [[Notiz_Keypoints and Descriptors#SIFT Descriptor SIFT-Descriptor|SIFT Descriptor]] 
## 3. Descriptor matching 
- Matching 
	- Calculate the distances between the feature vectors 
	- search similar keypoint descriptors 
	- and use the most similar feature vectors as corresponding points 
## 4. Stitching 
- Use a set of 8 corresponding points to define an equation system. 
- Solve the equation system to calculate the transformation parameter. 
- Use the transformation matrix to align one image into the other image. 

## Anforderung 
Region extraction needs to be repeatable and accurate 
- Ein Punkt ist **invariant** gegenüber Translation, Rotation und Skalierung
	- Zum Beispiel bleibt eine Ecke oder ein Kreuzungspunkt zweier Linien auch dann bestehen, wenn das Bild verschoben, gedreht oder skaliert wird. 
- Punkte können robust gegenüber affine Transformationen sein 
- Ein Feature-Detektor kann robust gegenüber Beleuchtungsänderungen oder leichtem Rauschen sein 


# SIFT Detector^SIFT-Detector
## Step 1: Gaussian and Difference-of-Gaussian pyramid 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_18-03-31.png?raw=" width="60%" /> 

- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_21-25-47.png?raw=" width="60%" /> 
- scale: Grad der Unschärfe. Ein größerer "scale" entspricht einer größeren Entfernung beim Betrachten, wodurch das Bild unschärfer und kleiner wird. 
- octave: Jede "octave" besteht aus einer Gruppe von Bildern, die die gleiche Größe haben, aber unterschiedliche Unschärfe (verschiedene "scales") aufweisen. 

## Step 2: Detect Minima and Maxima 
<img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_21-44-43.png?raw=" width="40%" /> 
- A point is selected as keypoint if it is higher or lower than all 26 (3 x 3 x 3 - 1) neighbors. 
- $\sigma$ : the smaller of the two gaussian images from the DoG image 

## Step3: Select Keypoints 
- Keypoints mit geringem Kontrast werden eliminiert 

## Step4: Eliminate false edges 
- Anpassung an grundlegende Kurven 

# SIFT Descriptor^SIFT-Descriptor
- ein Vektor, der alle Merkmale zu diesem Keypoint beinhaltet. Der Vektor hat eine Dimension von 4 × 4 × 8 = 128, somit 128 Merkmale. 

## Step 1: Detect Keypoint orientation 
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

## Step 2: Description 
- Define a squared 16x16 region around the keypoint, divide the region into 16 equal blocks by 4x4 pixel 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_22-15-22.png?raw=" width="30%" /> 
- Rotate the region according to the keypoint orientation 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_22-22-03.png?raw=" width="80%" /> 
- 16 blocks x 8 directions/block = 128 directions $\Rightarrow$ SIFT Descriptor $\left(\begin{array}{c}m_{1} \\\vdots \\m_{128}\end{array}\right)$ 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-09_22-24-00.png?raw=" width="30%" /> 



# Harris Corner Detector^Harris-Corner-Detector
## mathematical principle 
- Consider shifting the window W by (u,v) 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_12-20-05.png?raw=" width="20%" /> 
- Sum of Square Differences (SSD) 
	- $\begin{array}{l}E(u, v) & =\sum_\limits{(x, y) \in W}[I(x+u, y+v)-I(x, y)]^{2} \\        & \approx \sum_\limits{(x, y) \in W}[u ~ v]\left[\begin{array}{cc}I_{x}^{2} & I_{x} I_{y} \\I_{y} I_{x} & I_{y}^{2}\end{array}\right]\left[\begin{array}{l}u \\v\end{array}\right]\end{array}$ 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_12-27-35.png?raw=" width="70%" /> 
## Step 1: Measure SSD 
<img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_12-34-59.png?raw=" width="60%" /> 
- $E \approx\left[\begin{array}{ll}u & v\end{array}\right] ~ M ~ \left[\begin{array}{l}u \\v\end{array}\right]$ 
## Step 2: Compute M 
- $\begin{array}{l}M &=\sum_{x, y} w(x, y)\left[\begin{array}{cc}I_{x}^{2} & I_{x} I_{y} \\I_{x} I_{y} & I_{y}^{2}\end{array}\right] \\&= R^{-1}\left[\begin{array}{cc}\lambda_{1} & 0 \\0 & \lambda_{2}\end{array}\right] R\end{array}$ 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_12-49-38.png?raw=" width="30%" /> 
## Step 3: Classification of image points using Eigenvalues 
<img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_12-53-58.png?raw=" width="50%" /> 
### Corner Response Function 
- $\begin{array}{l}R &=\operatorname{det}(M)-\alpha \operatorname{trace}(M)^{2} \\&=\lambda_{1} \lambda_{2}-\alpha\left(\lambda_{1}+\lambda_{2}\right)^{2}\end{array}$ 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_12-57-22.png?raw=" width="50%" /> 
## Eigenschaften 
- **invariant** to image rotation 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_13-04-05.png?raw=" width="30%" /> 
	- Shape / Eigenvalues remain the same 
- **variant** to image scale 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_13-05-35.png?raw=" width="50%" /> 

# Hessian Detector^Hessian-Detector
- erfasst Bereiche mit **schnellen Helligkeitsänderungen** 
- Um Merkmale zu identifizieren, wird die Determinante der Hessian-Matrix an jedem Pixel berechnet. Ein **hoher** Wert der **Determinante** zeigt einen starken Helligkeitsunterschied und damit einen potenziellen **Merkmalsbereich** an. 
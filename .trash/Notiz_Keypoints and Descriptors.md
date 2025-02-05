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
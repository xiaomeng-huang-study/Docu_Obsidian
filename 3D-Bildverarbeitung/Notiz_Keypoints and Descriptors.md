<img src="https://github.com/ICH-BIN-HXM/images_3DBV/blob/main/Scrennshot_2024-11-08_22-24-56.png?raw=" width="90%" /> 

# Image Stitching 
## 1. Keypoint Localization 
- Keypoint (feature point / interesting point) 
	- charakteristische Punkte in einem Bild, die eindeutig und konsistent in verschiedenen Ansichten oder unter verschiedenen Beleuchtungsbedingungen erkannt werden können. 
	- z.B. Ecken, Kanten, Blob, Textur- oder Musterbereiche 
## 2. Keypoint Description 
- Keypoint descriptor 
	- save the neighborhood informations around a keypoint as a description of the object, usually as feature vectors 
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


# SIFT detector and descriptor 
## Step 1: Gaussian and Difference-of-Gaussian pyramid 
<img src="https://github.com/ICH-BIN-HXM/images_3DBV/blob/main/Scrennshot_2024-11-09_18-03-31.png?raw=" width="60%" /> 

<img src="https://github.com/ICH-BIN-HXM/images_3DBV/blob/main/Scrennshot_2024-11-09_21-25-47.png?raw=" width="60%" /> 
## Step 2: Detect Minima and Maxima 
<img src="https://github.com/ICH-BIN-HXM/images_3DBV/blob/main/Scrennshot_2024-11-09_21-44-43.png?raw=" width="40%" /> 
- A point is selected as keypoint if it is higher or lower than all 26 (3 x 3 x 3 - 1) neighbors. 
## Step 3: Detect Keypoint orientation 

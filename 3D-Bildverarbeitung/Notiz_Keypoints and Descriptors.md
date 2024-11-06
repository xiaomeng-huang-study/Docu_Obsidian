# feature points / interesting points 
- Definition 
	- charakteristische Punkte in einem Bild, die eindeutig und konsistent in verschiedenen Ansichten oder unter verschiedenen Beleuchtungsbedingungen erkannt werden können. 
- Beispiele 
	- Ecken 
	- Kanten 
	- Blob 
	- Textur- oder Musterbereiche 

# Image Stitching 
## 1. Keypoint Localization 
## 2. Keypoint Description 
- Describe the feature points with local area informations and save the informations in a feature vector 
## 3. Descriptor matching 
- Calculate the distances between the feature vectors and use the most similar feature vectors as corresponding points 
## 4. Stitching 
- Use a set of 8 corresponding points to define an equation system. Solve the equation system to calculate the transformation parameter. Use the transformation matrix to align one image into the other image. 
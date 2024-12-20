# Aging Filter 
- 1. img1 = read wrinkle image 
- 2. img2 = read input face image 
- 3. Find landmarks in img1 and img2 
- 4. Find Delaunay triangulation for img1 
- 5. For each triangle: Warp wrinkle image to input face image 
- 6. Calculate the face mask for seamless cloning 
- 7. Seamlessly clone the wrinkle image onto original face 


## Estimation of Forehead points 
### Train a new landmark detector with points on the forehead 
### Estimate the forehead points based on the current landmark points 
- Find the convex hull of Facial landmarks 
	- <img src="https://github.com/xiaomeng-huang-study/images_DLACV/blob/main/Scrennshot_2024-11-14_22-04-40.png?raw=" width="90%" /> 
- Offse 
	- <img src="https://github.com/xiaomeng-huang-study/images_DLACV/blob/main/Scrennshot_2024-11-14_22-07-06.png?raw=" width="80%" /> 

## Seamless Image Cloning 
- Calculate the gradients from the ROI in Image 2 
- Calculate the gradients from the ROI in Image 1 
- Make the gradients as close to source Image 1 as possible 
- Solving the **Poisson Equation** results in same boundary pixel values 

# Face Swap 
- 1. Face Alignment 
- 2. Find Convex Hull 
- 3. Delaunay Triangulation of Convex Hull points 
- 4. Affine warping of triangles 
- 5. Blending of images with Seamless Cloning 

# Non-linear Deformations 
# 2D planar Transformations 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-02-20.png?raw=" width="90%" /> 
## Rigid Transformation : 2D Rotation and Translation 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-05-56.png?raw=" width="50%" /> 
- DoF = 3 

## Similarity Transformation : 2D Rotation, Scaling and Translation 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-07-42.png?raw=" width="40%" /> 
- DoF = 4 

## Affine Transformation : 2x2-Matrix and Translation 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-08-59.png?raw=" width="30%" /> 
- DoF = 6
## Projective Transformation 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-10-30.png?raw=" width="30%" /> 
- DoF = 8 

## Multiple Transformations 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-22-00.png?raw=" width="40%" /> 

# Warping 
## Linear Warping: Affine Transformation 
## Non-linear Warping: by a non-linear mapping function M 

## Face Morphing 
### 1. Facial Landmark Detection 
- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-57-00.png?raw=" width="60%" /> 
- 68 landmark points + 8 points on the boundary of both images 
### 2. Normalize the face image sizes 
- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-38-26.png?raw=" width="30%" /> 
- Normalize the faces and transform them to the same coordinate system. 
### 3. Delaunay Triangulation 
- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-40-34.png?raw=" width="70%" /> 
- Find the triangles from 4 vertices, so that the circumcircle from 3 points doesn‘t include the 4th point.
	- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-51-00.png?raw=" width="90%" /> 
- Delaunay Triangulation for each 76 points 
- Result: Use the average of the two point sets. 
### 4. Warping Images and Alpha Blending 
1. Calculate the affine transforms for: a triangle from image 1 and the corresponding triangle from the morphed image and do the same for image 2. 
2. Warp triangles: Use the calculated affine transforms for every triangle to get a warped version for image 1 and a warped version for image 2. 
3. Alpha blend warped images 
	- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_21-44-39.png?raw=" width="30%" /> 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_22-01-00.png?raw=" width="50%" /> 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_22-02-00.png?raw=" width="50%" /> 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_22-04-00.png?raw=" width="50%" /> 

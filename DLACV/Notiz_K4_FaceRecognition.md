# Training 
- Convert a fixed size face image into a vector 
	- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-11-10_21-45-50.png?raw=" width="70%" /> 
- **Triplet Loss** 
	- vergleicht 
		- ein Anchor-Bild (das Referenzbild) 
		- ein Positive-Bild (ein Bild der gleichen Person) 
		- ein Negative-Bild (ein Bild einer anderen Person) 
	- versucht, den Abstand zwischen Anchor und Positive zu verkleinern und den Abstand zwischen Anchor und Negative zu vergrößern. 
	- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-11-10_22-00-14.png?raw=" width="90%" /> 
- **Enrollment** 
	- enroll / add a new person 
- **Inference** 
	- KNN 
		- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-11-10_22-02-15.png?raw=" width="70%" /> 


# Face Recognition with Eigenfaces 
## Step 1: Face Detection and Normalization 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-11-11_21-11-40.png?raw=" width="50%" /> 
- detect the face image 
- align the face image with the left and right eye corner points 
- normalize the image size to 64x64 
## Step 2: Vectorization 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-11-11_21-12-18.png?raw=" width="30%" /> 
- Convert normalized face into a vector 
## Step 3: Reduce the dimensionality 
- Average Face (Mean Vector): $\mu=\frac{1}{m}\sum_{i=1}^{m} g_{i}$ (m: number images) 
- Difference from the average face: $X=\left[\left(g_{1}-\mu\right)\left(g_{2}-\mu\right) \ldots\left(g_{m}-\mu\right)\right]$ 
## Step 4: Covariance matrix $C^{\prime}$ 
- $C^{\prime}=\frac{1}{m} X^{T} X$ 
- The Eigenvalues from $C^{\prime}$ are the same as the top m eigenvalues of $C$. 
- Eigenvectors $v_{i}^{\prime} = Xv_{i}^{\prime}$ 
- Eigenface: $\text { eigenface }_{i}=\frac{v_{i}}{\left\|v_{i}\right\|}$ 
## Step 4: Weight vector $w_{k}$ 
- $w_{k}=\boldsymbol{v}_{\boldsymbol{k}}^{T} \boldsymbol{X}_{\boldsymbol{i}}$ 
## Step 5: New Face Recognition 
- convert new face to a vector $\Rightarrow$ subtract the average face $\Rightarrow$ project it into the eigenfaces space $\Rightarrow$ obtain its weight vector. 
- Compare these projection coefficients to those stored in the database to find the most similar face. 
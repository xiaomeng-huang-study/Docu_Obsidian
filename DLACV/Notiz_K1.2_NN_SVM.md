# Linear Decision Boundaries 
- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-28_20-24-04.png?raw=" width="60%" /> 
- Definition: A Linear Decision Boundary in n-D space is a (n-1)-D Plane. 
- Evaluation 
	- Margin or Safe Zone 
		- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-28_20-29-45.png?raw=" width="30%" /> 
		- Definition: The width that the boundary could be increased before hitting a feature point. 


# Support Vector Machine (SVM) 
## Support Vectors 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-28_20-35-24.png?raw=" width="30%" /> 
- Definition: Closest data samples to the boundary 
## SVM 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-28_20-39-44.png?raw=" width="60%" /> 
- Classifier optimized to Maximize the Margin 
## Finding Decision boundary (W,b) 
- For each training sample $(f_j, \lambda_j)$ 
	- if $\lambda_{i}=+1: \mathbf{w}^{T} \mathbf{f}_{i}+b \geq \frac{\rho}{2}$ or $\lambda_{i}=-1: \mathbf{w}^{T} \mathbf{f}_{i}+b \leq-\frac{\rho}{2}$ $\Rightarrow$ $\lambda_{i}\left(\mathbf{w}^{T} \mathbf{f}_{i}+b\right) \geq \frac{\rho}{2}$ 
- For each support vector $s$ 
	- $\lambda_{i}\left(\mathbf{w}^{T} \mathbf{f}_{i}+b\right) = \frac{\rho}{2}$ 
## Use SVM 
<img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-28_21-25-27.png?raw=" width="50%" /> 

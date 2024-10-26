# Viola Jones Algorithm 
## 1. Feature Selection using Haar-like Features 
## 2. Feature Selection with AdaBoost 
## 3. Cascade of Classifiers 
## 4. Multi-Scale Detection and Sliding Window 

## Haar-Like Features 
- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_15-52-50.png?raw=" width="70%" /> 
- Concept 
	- Compare pixel values to detect lighter and darker regions in an image. 
- Types 
	- Edge Features: Detect edges by comparing adjacent pixel regions. 
	- Line Features: Identify lines using pixel contrasts. 
	- Four-sided Features: Useful for detecting diagonal shapes. 
- Similarities 
	- Convert RGB to gray value image 
	- Low values represent dark clusters (ie. Eyes) 
	- High values represent bright clusters (ie. Nose) 
- Computation cost 
	- without Integral Image 
		- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_16-00-55.png?raw=" width="80%" /> 
	- with Integral Image 
		- Integral Image 
			- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_16-02-19.png?raw=" width="50%" /> 
		- <img src="https://github.com/ICH-BIN-HXM/images_DLACV/blob/main/Scrennshot_2024-10-26_16-03-05.png?raw=" width="60%" /> 


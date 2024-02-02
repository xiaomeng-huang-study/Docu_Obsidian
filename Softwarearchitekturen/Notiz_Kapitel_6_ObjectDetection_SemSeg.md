- Computer Vision Tasks 
	- Classification 
	- Semantic Segmentation 
	- Object Detection 
	- Instance Segmentation 

# Semantic Segmentation 
- wird jedes <u>Pixel</u> in einem Bild einer bestimmten <u>Klasse</u> oder Kategorie zugeordnet, um eine präzise Segmentierung des Bildes in verschiedene semantische Regionen zu ermöglichen.
- Fully Convolutional 
	- downsampling 
	- upsampling 
		- not learnable 
			- Unpooling 
				- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-02_22-03-09.png?raw=" width="500" /> 
			- Max Unpooling 
				- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-02_22-02-32.png?raw=" width="300" /> 
		- learnable 
			- Transpose Convolution 
				- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-02_22-01-10.png?raw=" width="400" /> 
- Beispiel 
	- U-Net 


# Object Detection 
- Input: RGB Image 
- Output: A set of detected objects 
	- Category label -> "WAS" 
	- Bounding box: x, y, width, height "WO" 
## Region-Based CNN (R-CNN) 
- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-02_22-08-10.png?raw=" width="600" /> 
- Schritte 
	- Regions of Interest (RoI) 
	- Warp: modify size 
	- ConvNet 
	- Classify + Bounding Box Regression 
- Nachteil 
	- zu langsam 

## Fast R-CNN 
- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-02_22-17-03.png?raw=" width="600" /> 
- Schritte 
	- "Backbone" Network e.g. AlexNet, VGG, ResNet 
		- most computation 
	- Regions of Interest (RoI) 
	- [[Notiz_Kapitel_6_ObjectDetection_SemSeg#Crop|Crop]] + Resize 
	- Per-Region Network 
		- lightweight 
	- Classify + Bounding Box Regression 

## Crop 
### RoI Pool 
- den nächstgelegenen Punkt in der Feature Map suchen und Gesamtverschiebung 
- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-02_22-33-22.png?raw=" width="200" /> 
- 
### RoI Align 

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
- Typen 
	- two-stage 
		- [[Notiz_Kapitel_6_ObjectDetection_SemSeg#Region-Based CNN (R-CNN)|RCNN]] and SPPNet (2014) 
		- [[Notiz_Kapitel_6_ObjectDetection_SemSeg#Fast R-CNN|Fast RCNN]] and [[Notiz_Kapitel_6_ObjectDetection_SemSeg#Faster R-CNN|Faster RCNN]] (2015) 
		- Mask R-CNN (2017) 
		- Pyramid Networks/FPN (2017) 
		- G-RCNN (2021) 
	- single-stage 
		- YOLO (2016) 
		- SSD (2016) 
		- RetinaNet (2017) 
		- YOLOv3 (2018) 
		- YOLOv4 (2020) 
		- YOLOR (2021) 
		- YOLOv7 (2022) 
		- YOLOv8 (2023) 

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

### Crop 
#### RoI Pool 
- den nächstgelegenen Punkt in der Feature Map suchen und Gesamtverschiebung 
- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-02_22-33-22.png?raw=" width="200" /> 
- 
#### [RoI Align](https://firiuza.medium.com/roi-pooling-vs-roi-align-65293ab741db) 
- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-02_22-47-50.png?raw=" width="600" /> 

## Faster R-CNN 
- [[Notiz_Kapitel_6_ObjectDetection_SemSeg#Region Proposal Network (RPN)|Region Proposal Network (RPN)]] importiert 
- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-02_23-18-14.png?raw=" width="600" /> 
- Schritte 
	- RPN classification: anchor box is object / not an object 
	- RPN regression: predict transform from anchor box to proposal box 
	- Object classification: classify proposals as background / object class 
	- Object regression: predict transform from proposal box to object box 

### [Region Proposal Network (RPN)](https://medium.com/@codeplumber/region-proposal-network-rpn-backbone-of-faster-r-cnn-4a744a38d7f9) 
- liefert Proposals 


# Einschub 
## [Mean Average Precision (mAP)](https://www.dropbox.com/scl/fi/3c6xvrguouzdhvxti9tkj/sofarki_Notiz_MeanAveragePrecision.pdf?rlkey=az01u65bajdypz6cy0kfa5cbr&dl=0) 

## Intersection over Union (IoU) 
- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Scrennshot_2024-02-02_23-27-43.png?raw=" width="400" /> 
- ${\text IoU} = \frac{{\text Area~of~Intersection}}{{\text~Area~of~Union}}$ 
	- Area of Union: gesamte Fläche 

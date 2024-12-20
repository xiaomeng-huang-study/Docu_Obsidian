# GoogLe-Net 

- Inception module 
	- Naive Inception module 
		- Schaubild <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-20_20-37-56.png?raw=" width="400" /> 
		- 1x1 conv lernt Muster über die Tiefe der Eingabe 
		- 3 x 3 conv und 5 x 5 conv lernt räumliche Muster über alle Dimensionskomponenten (height, width and depth) der Eingabe 
		- Probleme 
			- Ausgabegrößen vom einzelnen Filter unterschiedlich $\Longrightarrow$ Padding 
			- Zu viel Ausgabenklassen bzw. zu viel Speicherplatz verbraucht $\Longrightarrow$ Hinzufügen der 1 x 1 "bottleneck" layers 
	- Inception module with dimension reduction 
		- Schaubild <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-11-20_20-45-24.png?raw=" width="400" /> 
		- 1 x 1 conv dient zur Dimensionsreduzierung 
- Merkmale 
	- Inception-Modul, wo "Bottleneck"-Layer die Dimension / räumliche Auflösung reduziert und die Auflösung in Tiefe erhöht 
	- Anzahl der klassischer FC-Layers reduziert 
- Vorteile 
	- Parameter gespart 
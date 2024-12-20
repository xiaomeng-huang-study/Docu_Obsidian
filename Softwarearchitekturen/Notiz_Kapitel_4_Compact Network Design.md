# Einschube für Compact Network Design 
## Depthwise Separable Convolutions 
- Veranschaulichung: <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-05_11-58-00.gif?raw=" width="600" /> 
- Struktur: <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-05_12-15-30.png?raw=" width="400" /> 
- Schritte: <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-05_12-22-56.png?raw=" width="600" /> 
- <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-05_12-41-21.png?raw=" width="350" /> 

## Bottleneck 


# Mobile-Net 
## V1 
- DW-Conv wird erst verwendet 
## V2 
- auf Basis von V1, Inverted Residuals wird erst verwendet 
- Inverted Residuals 
	- Schaubild: <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-06_20-03-56.png?raw=" width="700" /> 
		- Expansion-factor $t$ 
	- Expansion - Faltung - Kompression / Projection (in Form Schiffchen 梭形) 
	- Dimension $\uparrow$ mit 1×1-Conv -> DW-Faltung zur Extraktion der Merkmale (3×3) -> Dimension $\downarrow$ mit 1×1-Conv 
	- ReLU6-Aktivierungsfunktion + lineare Aktivierungsfunktion 
		- ReLU6: <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-06_20-13-47.png?raw=" width="300" /> 
	- im Vergleich mit Residual Block 
		- Kompression - Faltung - Expansion / Projection (in Form einer Sanduhr 沙漏) 
		- Dimension  $\downarrow$ mit 1×1-Conv -> normale Faltung zur Extraktion der Merkmale (3×3) -> Dimension $\uparrow$ mit 1×1-Conv 
		- ReLU-Aktivierungsfunktion 


# Efficient-Net 
- Individual upscaling 
	- Typen 
		- Erhöhung der Netzwerksbreite 
			- more feature-maps / filters 
			- Vorteile 
				- eine größere Vielfalt an Merkmalen zu lernen und kann daher komplexere Muster in den Daten erfassen 
			- Nachteile 
				- Overfitting-Gefahr 
		- Erhöhung der Netzwerkstiefe 
			- more convolutional layers 
			- Vorteile 
				- spezifischere und diskriminierendere Merkmale extrahieren 
				- Bessere Generalisierung 
			- Nachteil 
				- Vanishing Gradient Problem 
		- Erhöhung der Auflösung 
			- Bilder sowie feature-maps haben eine größere Breite und Höhe 
	- Probleme 
		- wenn das Modell bereits ausreichend groß ist, nehmen die Vorteile einer weiteren Skalierung in diesen Dimensionen ab. 
		  -> Asymptote 
- Compound scaling 
	- <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-08_14-04-19.png?raw=" width="500" /> 
		- Netzwerktiefe x 2 $\Rightarrow$ FLOPS x 2 
		- Breite oder Auflösung x 2 $\Rightarrow$ FLOPS x 4 
			- denn in $D_{K} \cdot D_{K} \cdot M \cdot N \cdot D_{F} \cdot D_{F}$ werden M und N verdoppelt 
	- Schritte 
		- $\phi = 1$ , $\alpha, \beta, \gamma$ zu bestimmen 
		- $\alpha, \beta, \gamma$ fest, $\phi$ nach HW anzupassen 
			- <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-08_14-47-25.png?raw=" width="350" /> 

# Quantisierung 
- die <u>Parameter und Aktivierungswerte</u> eines neuronalen Netzwerks von Gleitkommazahlen <u>in niedrigere Bitbreiten</u> oder Festkommazahlen umgewandelt werden, um <u>Speicherplatz und Berechnungskosten zu sparen</u>. 
- <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-08_15-17-00.png?raw=" width="700" /> 

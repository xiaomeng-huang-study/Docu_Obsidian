# Einschube für Compact Network Design 
## Depthwise Separable Convolutions 
- Veranschaulichung: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-05_11-58-00.gif?raw=" width="600" /> 
- Struktur: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-05_12-15-30.png?raw=" width="400" /> 
- Schritte: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-05_12-22-56.png?raw=" width="600" /> 
- <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-05_12-41-21.png?raw=" width="350" /> 

## Bottleneck 

# Mobile-Net 
## V1 
- DW-Conv wird erst verwendet 
## V2 
- auf Basis von V1, Inverted Residuals wird erst verwendet 
- Inverted Residuals 
	- Schaubild: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-06_20-03-56.png?raw=" width="700" /> 
		- Expansion-factor $t$ 
	- Expansion - Faltung - Kompression / Projection (in Form Schiffchen 梭形) 
	- Dimension $\uparrow$ mit 1×1-Conv -> DW-Faltung zur Extraktion der Merkmale (3×3) -> Dimension $\downarrow$ mit 1×1-Conv 
	- ReLU6-Aktivierungsfunktion + lineare Aktivierungsfunktion 
		- ReLU6: <img src="https://github.com/ICH-BIN-HXM/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-06_20-13-47.png?raw=" width="200" /> 
	- im Vergleich mit Restliches Modul 
		- Kompression - Faltung - Expansion / Projection (in Form einer Sanduhr 沙漏) 
		- Dimension  $\downarrow$ mit 1×1-Conv -> normale Faltung zur Extraktion der Merkmale (3×3) -> Dimension $\uparrow$ mit 1×1-Conv 
		- ReLU-Aktivierungsfunktion 
# Efficient-Net 
- Individual upscaling 
	- deeper 
	- wider 
	- higher resolution 
- Compound scaling 
	- 
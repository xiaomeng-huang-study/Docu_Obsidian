# Diskretisierung 
## Ortsauflösung 
- Definition: Abbildung des Ortsbereiches (x,y) auf MxN Bildelementen (m,n) 
- $m=\left\lfloor M \cdot \frac{x-x_{\min }}{x_{\max }-x_{\min }}\right\rfloor \text { und } \quad n=\left\lfloor N \cdot \frac{y-y_{\min }}{y_{\max }-y_{\min }}\right\rfloor$ 
- Die Ortsauflösung des Bildes wird durch die Anzahl der Pixel je Zeile bzw. Spalte bestimmt 
	- z.B. 1920 Pixels x 1080 Pixels 
## Farbauflösung 
### Kontrastauflösung 
- $0 \leq I_{\text {red}}(m, n), I_{\text {green}}(m, n), I_{\text {blue}}(m, n) \leq I_{\max }$ 
- Definition: Die Kontrastauflösung bezieht sich auf die **Anzahl der verschiedenen Helligkeitsstufen**, die in jedem Farbkanal dargestellt werden können. 
### Quantisierung 
- Definition: die Begrenzung auf z.B. 256 Werte mit $\mathrm{I}_{\lambda} \in[0,255]$ bei 8-bit 

# Fehler bei der Digitalisierung 
## Aliasing 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-10-27_20-25-07.png?raw=" width="60%" /> 
## Moiré-Effekt 
- Definition: neue Linien (Moiré-Muster) durch Überlagerung von Rastern oder Linien entstehen. 
- Moiré-Muster treten insbesondere auf, wenn periodische Strukturen mit **Frequenzen abgetastet** werden, die **niedriger** sind als die **doppelte Frequenz der Strukturen** selbst. 
- Überwindung: Mit Frequenzen, die mehr als das Doppelte der maximalen Frequenz, die im Bild vorkommt, abtasten. 
- Warum 2-Fach? 
	- Nyquist-Shannonsche Abtasttheorem: $f_{\text {abtast }}>2\left(f_{\max }-f_{\min }\right)$ 
### Beispiel 
- Geg.: eine Strichzeichnung mit einer minimalen Linienbreite von 0.1 mm. Mit wie vielen Bildpunkten sollte ein Quadratmillimeter digitalisiert werden? 
- Lös.: 2 Abtastwerte /  0.1mm $\Rightarrow$ 20 Abtastwerte / 1mm $\Rightarrow$ 400 Bildpunkte / 1 $mm^2$ 

# Bildeigenschaften 
## Nachbarschaft 
### Quadratische Gitter 
- 4-er Nachbarschaft 
	- (x,y-1), (x, y+1), (x-1,y) und (x+1,y) 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-10-27_20-47-01.png?raw=" width="10%" /> 
- 8-er Nachbarschaft 
	- (x-1,y-1), (x+1,y-1), (x-1, y+1), (x+1,y+1) 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-10-27_20-47-43.png?raw=" width="10%" /> 
- 6-er Nachbarschaft 
	- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-10-27_20-48-33.png?raw=" width="10%" /> 
## Pfad 
- Definition: Folge von benachbarten Pixeln unter gleicher Homogenitätsbedingung (z.Bsp. gleicher Intensitätswert) 
## Zusammenhängendes Gebiet 
- Definition: Menge aller Pixel, zwischen denen Pfade existieren 
## Rand 
- Definition: Folge von Pixeln eines zusammenhängenden Gebiets, die zum Gebiet gehören und zu Pixeln benachbart sind, die nicht dazu gehören. 
## Distanzmaße 
### Euklidische Distanz 
- $D_{e}\left(x_{1}, y_{1}, x_{2}, y_{2}\right)=\sqrt{\left(x_{1}-x_{2}\right)^{2}+\left(y_{1}-y_{2}\right)^{2}}$ 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-10-27_20-56-38.png?raw=" width="20%" /> 
### Schachbrettdistanz bei 8-er Nachbarschaft 
- $D_{8}\left(x_{1}, y_{1}, x_{2}, y_{2}\right)=\max \left\{\left|x_{1}-x_{2}\right|,\left|y_{1}-y_{2}\right|\right\}$ 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-10-27_20-58-13.png?raw=" width="20%" /> 
### Manhattan-Distanz (Cityblock-Distanz) bei 4-er Nachbarschaft 
- $D_{4}\left(x_{1}, y_{1}, x_{2}, y_{2}\right)=\left|x_{1}-x_{2}\right|+\left|y_{1}-y_{2}\right|$ 
- <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-10-27_20-59-17.png?raw=" width="20%" /> 
# Direktes Volumenrendering (DVR) 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-02-02_15-54-10.png?raw=" width="90%" /> 
- 1. Daten-Sampling 
	- Entlang jedes Strahls (bei RayCasting) werden an regelmäßigen Abständen (Sampling-Punkten) die Voxelwerte abgetastet. 
- 2. Filterung (Interpolation) 
	- Da die Abtastpositionen in der Regel nicht identisch mit einer Voxelposition sind. 
	- trilinear interpolation <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-02-02_16-04-51.png?raw=" width="20%" /> 
- 3. Klassifikation 
	- Transferfunktion $\Rightarrow$ Farbe $C$ (RGB), Opazität $\alpha$ (transparent, semitransparent oder völlig undurchsichtig) für jedes Pixel 
	- Pre-Classification und Post-Classification 
		- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-02-02_16-18-02.png?raw=" width="40%" /> 
		- Post-Classification besser als Pre-Classification 
			- Farb- und Transparenzqualität: bei Post-Classification ohne Farbmischung 
			- Verlust von Details: bei Post-Classification gering, da alle Strahlwerte berücksichtigt werden; aber bei Pre-Classification Höher, da Transferfunktion nur auf diskrete Punkte wirkt. 
- 4. Komposition 
	- Alphablending 
	- Volumenintegral 
		- $I(s)=I\left(s_{0}\right) \cdot e^{-\tau\left(s_{0}, s\right)}+\int_{s_{0}}^{s} q(\tilde{s}) \cdot e^{-\tau(\tilde{s}, s)} d \tilde{s}$ 
			- $I(s_0)$ die initiale Intensität an der Stelle $s_0$ 
			- $q(\tilde{s})$ die Energie an der Stelle
			- $e^{-\tau}$ der Abschwächungsprozess durch die Absorption entlang des Lichtstrahls 
		- Back-to-Front 
			- $C_{d s t}=\left(1-\alpha_{s r c}\right) \cdot C_{d s t}+C_{s r c}$ 
				- $C_{d s t}$ die bisher akkumulierte Farbe 
				- $C_{s r c}$ die Farbe der aktuellen Schicht, die hinzugefügt wird 
				- Da die aktuellen Schicht immer sich vorne befindet $\rightarrow$ $C_{s r c}$ mit Gewicht 1; Die Transparenz $\alpha_{s r c}$ beeinflusst, wie viel von $C_{d s t}$ (den hinteren Schichten) noch sichtbar bleibt. 
		- Front-to-Back 
			- $\begin{aligned}C_{d s t} & =C_{d s t}+\left(1-\alpha_{d s t}\right) \cdot C_{s r c} \\\alpha_{d s t} & =\alpha_{d s t}+\left(1-\alpha_{d s t}\right) \cdot \alpha_{s r c}\end{aligned}$ 
				- $C_{d s t}$ die bisher akkumulierte Farbe 
				- $C_{s r c}$ die Farbe der aktuellen Schicht, die hinzugefügt wird 
				- addiert die Farbe der aktuellen Schicht $C_{s r c}$​, gewichtet durch die Transparenz der bisherigen Schichten $\left(1-\alpha_{d s t}\right)$ 
			- Early Ray Termination 
				- der Strahl wird **frühzeitig gestoppt**, wenn genug Informationen gesammelt wurden und es keine weiteren sichtbaren Beiträge zur Endfarbe gibt. 


# Parameter des Systems 
- Die Position, Intensität und Richtung von externen Lichtquellen 
- Sampling-Rate 
- Transferfunktion 


# Indirektes Volumenrendering (IVR) 
## Marching Cubes Algorithmus 
### Input 
- 3D-Skalarfeld auf einem regulären Voxel-Gitter 
- Iso-Wert 

### Verarbeite jeden Würfel (Cube) im Gitter 
- 1. Klassifiziere die Eckpunkte des Würfels 
	- größer oder gleich dem Iso-Wert ist, wird der Eckpunkt als außen klassifiziert. 
	- kleiner als der Iso-Wert ist, wird der Eckpunkt als innen klassifiziert. 
- 2. Berechne den **Index** des Würfels 
	- 8-Bit-Zahl ist der **Index** des Würfels (Wert zwischen 0 und 255). 
- 3. Hole die Dreieckskonfiguration aus der Lookup-Tabelle (LUT) 
	- eine vordefinierte Lookup-Tabelle (LUT), die für jeden möglichen Index (0–255) die entsprechende Dreieckskonfiguration enthält. 
- 4. Approximiere die Schnittpunkte auf den Kanten 
	- der genaue Schnittpunkt der Isofläche mit der Kante wird durch lineare Interpolation der Skalarwerte an den beiden Eckpunkten der Kante berechnet. 
- 5. Berechne die Gradienten an den Vertices 
	- $\begin{array}{l}G_{x}(i, j, k)=\frac{D(i+1, j, k)-D(i-1, j, k)}{2\cdot\Delta  x} \\G_{y}(i, j, k)=\frac{D(i, j+1, k)-D(i, j-1, k)}{2\cdot\Delta  y} \\G_{z}(i, j, k)=\frac{D(i, j, k+1)-D(i, j, k-1)}{2\cdot\Delta  z}\end{array}$ 
- 6. Berechne die Normalenvektoren für die Dreiecke 
	- $N_{e}=\frac{\rho-D_{0}}{D_{1}-D_{0}} \cdot\left(N_{1}-N_{0}\right)+N_{0}$ 


# Unterschiede zwischen DVR und IVR 
| **Kriterium**          | **Direktes Volumenrendering**        | **Indirektes Volumenrendering**      |
| ---------------------- | ------------------------------------ | ------------------------------------ |
| **Darstellung**        | Gesamtes Volumen inkl. Transparenz   | Nur explizite Oberflächen            |
| **Berechnungsaufwand** | Höher                                | Niedriger                            |
| **Datenverarbeitung**  | Ohne vorherige Oberflächenextraktion | Mit vorheriger Oberflächenextraktion |
| **Innere Strukturen**  | Sichtbar                             | Nicht sichtbar                       |
| **Beispiele**          | CT/MRT-Scans, Flüssigkeitssimulation | 3D-Druck, Oberflächenmodellierung    |

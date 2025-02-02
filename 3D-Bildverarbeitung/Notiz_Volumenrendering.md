- IVR aufwendiger als DVR, wenn die Position der Kamera sich verändert 

Ray neu berechnen, wenn sich die Kamera bewegt: 
Eingangsdaten: Datensatz, sample rate, lichtpose, Transferfunktion 


# Direktes Volumenrendering (DVR) 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-02-02_15-54-10.png?raw=" width="90%" /> 
- 1. Daten-Sampling 
	- Entlang jedes Strahls (bei RayCasting) werden an regelmäßigen Abständen (Sampling-Punkten) die Voxelwerte abgetastet. 
- 2. Filterung (Interpolation) 
	- Da die Abtastpositionen in der Regel nicht identisch mit einer Voxelposition sind. 
	- trilinear interpolation <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-02-02_16-04-51.png?raw=" width="20%" /> 
- 3. Klassifikation 
	- Transferfunktion $\Rightarrow$ Farbe $C$, Opazität $\alpha$ für jedes Pixel 
	- Pre-Classification und Post-Classification 
		- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-02-02_16-18-02.png?raw=" width="40%" /> 
		- Post-Classification besser als Pre-Classification 
			- Farb- und Transparenzqualität: bei Post-Classification ohne Farbmischung 
			- Verlust von Details: bei Post-Classification gering, da alle Strahlwerte berücksichtigt werden; aber bei Pre-Classification Höher, da Transferfunktion nur auf diskrete Punkte wirkt. 
- 4. Komposition 
	- Alphablending 
	- Volumenintegral 
		- 



# Unterschiede zwischen Direkten und Indirekten Volumenrendering 
| **Kriterium**          | **Direktes Volumenrendering**        | **Indirektes Volumenrendering**      |
| ---------------------- | ------------------------------------ | ------------------------------------ |
| **Darstellung**        | Gesamtes Volumen inkl. Transparenz   | Nur explizite Oberflächen            |
| **Berechnungsaufwand** | Höher                                | Niedriger                            |
| **Datenverarbeitung**  | Ohne vorherige Oberflächenextraktion | Mit vorheriger Oberflächenextraktion |
| **Innere Strukturen**  | Sichtbar                             | Nicht sichtbar                       |
| **Beispiele**          | CT/MRT-Scans, Flüssigkeitssimulation | 3D-Druck, Oberflächenmodellierung    |

# Rendering-Integral 
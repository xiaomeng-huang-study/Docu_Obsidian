# CNN 

## Begriffe 
- Padding 
	- Valid Padding: kein Padding hinzugefügt 
	- Same Padding: Padding am Rand füllen, damit die Ausgabe gleiche Größe wie Eingabe hat (wenn Stride = 1) 
- Stride 
	- Schrittweite, mit der der Filter (oder Kernel) über die Eingabe verschoben wird, wenn die Faltung durchgeführt wird. 


## Animation 
- Convolution 
	- <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Snipaste_2023-12-04_22-49-00.gif?raw=" width="600" /> 


## Wichtige Größen 
- Convolutional layers 
	- ==Ausgabe Größe==: $(n + 2p -f)/s + 1$ 
		- Padding: Füllen mit 1 Pixel am Rand (um 1 Pixel nach außen erweitern) $\Rightarrow$ p = 1 
		- Stride 1 $\Rightarrow$ s = 1 
		- Eingabe: n x n 
		- Filter: f x f 
	- ==Anzahl der Parameter== [(hilfreiche Erklärung)](https://stackoverflow.com/questions/42786717/how-to-calculate-the-number-of-parameters-for-convolutional-neural-network ) 
		- (Anzahl der Filter) x (Volumen der Filter + 1)
			- Volumen der Filter = (Filter Höhe) x (Filter Breite) x (Anzahl der Kanäle in Eingabe)
			- "+ 1": für den Bias-Term pro Filter 
		- eng.: (Number of Kernel) x (Kernel Volume + 1) 
	- ==Speicherbedarf== (Ausgabe dominiert) 
		- (Batch Size) x (Ausgabevolumen) x (Präzision) 
			- Präzision: z.B. float32 -> 32 Bit / dig. 
	- ==Rechenaufwand== / Flops 
		- (Volumen der Filter) x 2 x (Ausgabefläche) x (Anzahl der Filter) 
		- eng.: 2 x (Number of Kernel) x (Kernel Volume) x (Output area) 
- Fully-connected layers 
	- <img src="https://github.com/xiaomeng-huang-study/images_Softwarearchitekturen/blob/main/Scrennshot_2024-01-31_21-58-00.png?raw=" width="400" /> 
	- ==Anzahl der Parameter== 
		- Ausgabe Größe x (Eingabe Größe + 1) 
			- "+ 1": für den Bias-Term pro Neuron 
		- eng.: (Input Size) x (Output Size) + Output Size 
	- ==Speicherbedarf== (Parameter dominiert) 
		- (Batch Size) x (Anzahl der Parameter) x (Präzision) 
	- ==Rechenaufwand== / Flops 
		- 2 x (Eingabegröße) x (Ausgabegröße) 
		- eng.: 2 x (Input Size) x (Output Size) 
### Eigenschaften 
- Anzahl der Parameter: voll verknüpfte Schichten > Faltungsschichten 
- Rechenaufwand (Flops): Faltungsschichten >> voll verknüpfte Schichten 
### Anmerkungen 
- Filter = Kernel 
- Anzahl der Kanäle in Eingabe = Anzahl der Kanäle pro Filter 
- Anzahl der Filter = Anzahl der Ausgabeklassen 

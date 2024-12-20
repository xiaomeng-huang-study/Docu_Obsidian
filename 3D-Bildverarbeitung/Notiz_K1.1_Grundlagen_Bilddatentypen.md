# Digitales Foto 
- Definitionsbereich: $x_{\min } \leq x \leq x_{\max }, \quad y_{\min } \leq y \leq y_{\max }, \quad \lambda_{\min } \leq \lambda \leq \lambda_{\max }$ 
- Wertebereich: $I_{\min } \leq I(x, y, \lambda) \leq I_{\max }$ 
	- z.B. $\lambda=\{\text { Rot, Grün, Blau }\}$ bei RGB, $I_{\text{max}}$ = 255 bei 8-bit 

# Bilddatentypen 
## Farbbild 
### RGB 
- 3 Kanal 
- Pro Kanal eine 2D-Pixel-Matrix/Array mit einem n-Bit-Wert pro Pixel 
## Graubild 
- 1 Kanal 
- nur eine 2D-Pixel-Matrix 
## Indexbilder mit Video Lookup Tabelle (VLT) 
- 1 Kanal 
- Indexbilder speichern pro Pixel nur einen Integer-Wert. 
- Dieser Wert ist ein Index, der auf eine Farbtabelle (VLT) verweist. 
- Die Farbtabelle speichert pro Index drei Farbwerte, i.d.R. normalisiert. 
- (Das Pixel wird dann entsprechend mit diesem RGB-Wert dargestellt.) 
- z.B. <img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-10-28_21-54-39.png?raw=" width="90%" /> 
## Schwarz/Weiß-Bilder / Binärbilder 
- 1 Kanal 
- Schwellenwert bei Schwarz/Weiß 
	- Grauwertmenge reduziert sich auf G = {0,1}, 1 Bit/Pixel 
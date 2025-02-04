- Definition: eine Methode, die Bewegung von Pixeln zwischen zwei aufeinanderfolgenden Bildern in einem Video zu schätzen. 

# Optical Flow equation 
- $I_{x} u+I_{y} v+I_{t}=0$ 
	- $I_x$ , $I_y$ , $I_t$ die partiellen ersten Ableitungen von $I$ in $x$ , $y$ and $t$ 
	- $u$ and $v$ : relative Geschwindigkeiten in x- und y-Richtung 

# Grafische Interpretation der Optical Flow-Gleichung 
- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-02-01_15-28-52.png?raw=" width="60%" /> 
- Normal Flow: Die Bewegungskomponente entlang des Helligkeitsgradienten 
- Parallel Flow: Die Bewegungskomponente entlang der Helligkeits-Isolinien 
- Beziehung mit Optical Flow Gleichung: Sie beschreibt ausschließlich den Normal Flow, während der Parallel Flow unbestimmt bleibt. 

# Solution to $u$ and $v$ 
- Zusatzbedingungen benötigt: eine Gleichung aber mit zwei Unbekannten 
## 1. Lucas Kanade 
- Zusatzbedingungen: Innerhalb einer kleinen Nachbarschaft (z.B. 3 × 3) um einen Punkt für den der Optische Fluss berechnet wird, bleibt der Geschwindigkeits-Vektor innerhalb der Nachbarschaft konstant. 
## 2. Horn Schunck 
- Zusatzbedingungen: Der Optical Flow ist glatt über das gesamte Bild (d. h., benachbarte Pixel haben ähnliche Bewegungsvektoren). 
## Comparison between Lucas Kanade and Horn Schunck 
<img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_17-59-52.png?raw=" width="90%" /> 

# Eigenschaften 
- used for very small pixel changes between two images 
- **variant** to scale 
- **not invariant** to rotation 

# Ausblick 
## Pyramid scheme 
<img src="https://github.com/xiaomeng-huang-study/images_3DBV/blob/main/Scrennshot_2024-11-10_18-06-00.png?raw=" width="90%" /> 

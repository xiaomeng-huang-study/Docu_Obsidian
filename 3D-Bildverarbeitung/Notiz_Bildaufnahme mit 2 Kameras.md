# Epipolare Geometrie 
<img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-27_21-49-00.png?raw=" width="50%" /> 

- Tiefeninformationen gewinnen: Wenn zwei Kameras dasselbe Objekt aus leicht unterschiedlichen Positionen aufnehmen, gibt es eine **Verschiebung (Disparität)** der Position des Objekts in den beiden Bildern. Diese Disparität hängt von der Tiefe des Objekts ab: Je näher das Objekt ist, desto größer ist die Verschiebung. Durch die Berechnung der Disparität kann die Tiefe des Objekts rekonstruiert werden. 


## Epipol (Epipole) 
- Definition: Der Epipol ist der Punkt in einem Bild, an dem die Projektion der anderen Kamera liegt. ($e_L,~e_R$) 

## Epipolarlinien (Epipolar Lines) 
- Definition: Eine Epipolarlinie in einem Bild ist die Projektion der Sichtlinie (der Linie, die den Kameramittelpunkt und einen Punkt in der Szene verbindet) der anderen Kamera auf dieses Bild. ($e_R-X_R$) 

## Epipolarebene (Epipolar Plane) 
- Definition: Die epipolare Ebene ist die Ebene, die durch die beiden Kameramittelpunkte und einen Punkt in der Szene (z.B. ein Objekt) aufgespannt wird. ($X-O_L-O_R$) 

## Epipolare Bedingung (Epipolar constraint) 
- Definition: Jeder Bildpunkt $p_i$ eines 3D Punktes $P$ liegt in den entsprechenden Bildebenen nur auf der korrespondierenden Epipolar-Geraden. 
- Mathematische Formulierung: $p^{t} F p^{\prime}=0$ 

## Fundamentalmatrix 
- Definition: Die beschreibt die geometrische Beziehung zwischen zwei Bildern, die von zwei Kameras aus unterschiedlichen Positionen aufgenommen wurden. 
- Bestimmung mit **8-Punkt-Algorithmus** 
	0. Normalisierung der Punkte 
	1. Konstruktion der $8 \times 9$ Matrix $Q$ 
		- $$\left[\begin{array}{lll}x_{i} & y_{i} & 1\end{array}\right]^{t}\left[\begin{array}{lll}f_{11} & f_{12} & f_{13} \\f_{21} & f_{22} & f_{23} \\f_{31} & f_{32} & f_{33}\end{array}\right]\left[\begin{array}{c}x_{i}^{\prime} \\y_{i}^{\prime} \\1\end{array}\right]=0$$
 
		- Linearisierung $$\left(\begin{array}{llllllllll}x_{i} x_{i}^{\prime} & x_{i} y_{i}^{\prime} & x_{i} & y_{i} x_{i}^{\prime} & y_{i} y_{i}^{\prime} & y_{i} & x_{i}^{\prime} & y_{i}^{\prime} & 1\end{array}\right)\left(\begin{array}{l}f_{11} \\f_{12} \\f_{13} \\f_{21} \\f_{22} \\f_{23} \\f_{31} \\f_{32} \\f_{33}\end{array}\right)=0$$ 
		- DoF = 8 ($f_{\text{33}}$ default = 1) $\Rightarrow$ 8 Gleichungen $$\left(\begin{array}{ccccccccc}x_{1} x_{1}^{\prime} & x_{1} y_{1}^{\prime} & x_{1} & y_{1} x_{1}^{\prime} & y_{1} y_{1}^{\prime} & y_{1} & x_{1}^{\prime} & y_{1}^{\prime} & 1 \\x_{2} x_{2}^{\prime} & x_{2} y_{2}^{\prime} & x_{2} & y_{2} x_{2}^{\prime} & y_{2} y_{2}^{\prime} & y_{2} & x_{2}^{\prime} & y_{2}^{\prime} & 1 \\\vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots \\x_{8} x_{8}^{\prime} & x_{8} y_{8}^{\prime} & x_{8} & y_{8} x_{8}^{\prime} & y_{8} y_{8}^{\prime} & y_{8} & x_{8}^{\prime} & y_{8}^{\prime} & 1\end{array}\right) \cdot \vec{f}=0$$ 
	2. Singulärwertzerlegung (SVD) von $Q^{T} \cdot Q$ 
		- $Q^{T} Q =U S V^{T}$  
		- Die Spalten von $V$ sind die Eigenvektoren von $Q^{T} Q$ 
	3. Einträge von $F$ aus der SVD extrahieren 
		- die letzte Spalte von $V$ $v_9$ entspricht dem kleinsten Singulärwert 
		- Forme $v_9$​ in eine $3\times3$ - Matrix $F$ um 
	4. Rang-2-Bedingung für $F$ erzwingen  
	5. Denormalisierung von $F$ 
- kann Epipolarlinien und Epipole beschreiben 
	- Epipolarlinien 
		- $l_{2}=F p_{1}$ , $l_{1}=F^{T} p_{2}$ 
		- Beispiel <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-27_23-14-05.png?raw=" width="60%" /> 
	- Epipole: $F e_1 = 0$, $F^{T} e_2 = 0$ 

## Essentialmatrix und Fundamentalmatrix 
### Essentialmatrix 
- ist unter der Annahme, dass die **intrinsischen Kameraparameter** bekannt sind. 
- Die beinhaltet nur Rotationen und Translationen zwischen den Kameras, d.h. nur die extrinsischen Parameter. 
- $p_{2}^{T} K_{2}^{-T} E K_{1}^{-1} p_{1}=0$ 

### Fundamentalmatrix 
- unabhängig von den intrinsischen Kameraparametern 
- $p_{2}^{T} F p_{1}=0$ 



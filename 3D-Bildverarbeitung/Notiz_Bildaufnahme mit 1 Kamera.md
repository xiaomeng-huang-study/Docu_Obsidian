# Unterschied zwischen WKS und KKS 

| Eigenschaft |         Weltkoordinatensystem (WKS)          |                 Kamerakoordinatensystem (KKS)                  |
| :---------: | :------------------------------------------: | :------------------------------------------------------------: |
| Definition  | Globales, festes Koordinatensystem der Szene |           Lokales, kamerabezogenes Koordinatensystem           |
|  Ursprung   |       Beliebig in der Szene festgelegt       | Im optischen Zentrum der Kamera (dem Loch im Lochkameramodell) |


# Definition von Modell einer Lochkamera 
Es besteht aus einem kleinen Loch auf der Vorderseite und einer Bildebene auf der Rückseite. Licht von einem Punkt in der Szene tritt durch das Loch und trifft auf die Bildebene, wodurch ein Bild entsteht. Das Lochkameramodell basiert auf dem Prinzip der **zentralen Projektion**, bei der alle Lichtstrahlen durch einen einzigen Punkt (das Loch) verlaufen. 


# Projektive Transformation 
<img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-26_20-07-49.png?raw=" width="60%" /> 
- beschreibt, wie Punkte im dreidimensionalen Raum auf eine zweidimensionale Bildebene projiziert werden. 


# Kameraparameter 
## Intrinsische Parameter 
- Definition: die **inneren Eigenschaften** der Kamera. Sie sind unabhängig von der Position und Orientierung der Kamera in der Szene. 

- <img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-26_20-09-56.png?raw=" width="60%" /> 
1. Focal length (Brennweite) : Die Brennweite $f$ ist der Abstand zwischen dem optischen Zentrum der Kamera (dem Loch im Lochkameramodell) und der Bildebene (dem Bildsensor) 
	- Eine größere Brennweite führt zu einer stärkeren Vergrößerung und einem engeren Sichtfeld (Teleobjektiv) 
	- Eine kleinere Brennweite führt zu einer geringeren Vergrößerung und einem weiteren Sichtfeld (Weitwinkelobjektiv) 
2. Offset (Versatz der Bildmitte): Im idealen Lochkameramodell wird angenommen, dass die optische Achse der Kamera genau durch den Mittelpunkt der Bildebene verläuft. In der Realität ist dies jedoch oft nicht der Fall. Dies wird durch die Parameter $c_x, c_y$ beschrieben. 
	- Dies führt zu einer **Verschiebung des Bilds** in horizontaler oder vertikaler Richtung. 
3. Pixel dimensions (Pixelgröße): Im idealen Modell wird angenommen, dass die Pixel auf der Bildebene quadratisch sind und eine einheitliche Größe haben. In der Realität können Pixel jedoch unterschiedliche Abmessungen in horizontaler und vertikaler Richtung aufweisen. Dies wird durch die skalierten Brennweiten $f_x$​ und $f_y$​ berücksichtigt. 
	- Dies kann zu einer **Verzerrung des Bilds** führen, z. B. zu einer Dehnung oder Stauchung in einer Richtung. 
4. Skewness (Verzerrung durch Schiefstellung): Im idealen Modell wird angenommen, dass die Pixelachsen (horizontal und vertikal) perfekt orthogonal zueinander stehen. In der Realität kann es jedoch vorkommen, dass die Achsen nicht genau rechtwinklig zueinander ausgerichtet sind, z.B. aufgrund von Fertigungsungenauigkeiten im Kamerasensor. Dies wird durch den Schiefheitsparameter $\alpha$ (auch "Skew" genannt) berücksichtigt. Der Schiefheitsparameter beschreibt, wie stark die Pixelachsen von der Orthogonalität abweichen. 
	- Wenn $\alpha \neq 0$, führt dies zu einer **schiefen Abbildung**, bei der die Pixelachsen nicht rechtwinklig zueinander stehen. 
5. Distortion (Verzerrungen) 
	- radiale Verzerrungen und tangentiale Verzerrungen 
	- Radiale Verzerrungen: Diese Verzerrungen treten auf, weil Lichtstrahlen, die weiter von der optischen Achse entfernt sind, stärker gebrochen werden als Lichtstrahlen nahe der Achse. Dies führt zu einer **tonnenförmigen** (Verzerrung nach außen) oder **kissenförmigen** (Verzerrung nach innen) Verzerrung des Bilds. 
	- Tangentiale Verzerrungen: Diese Verzerrungen treten auf, wenn die Linsen nicht perfekt parallel zum Bildsensor ausgerichtet sind. Sie führen zu einer **schiefen Abbildung**. 

## Extrinsische Kameraparameter 
- Definition: **Position und Orientierung** der Kamera relativ zum Weltkoordinatensystem (WKS) 

## Bestimmung der Kameraparameter 
<img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-26_20-11-07.png?raw=" width="50%" /> 


# Kalibrierung mit Tsai 
## Projektionsgleichung 
$$\left[\begin{array}{l}u \\v \\1\end{array}\right]= \left(\begin{array}{llll}m_{11} & m_{12} & m_{13} & m_{14} \\m_{21} & m_{22} & m_{23} & m_{24} \\m_{31} & m_{32} & m_{33} & m_{34}\end{array}\right) \cdot\left[\begin{array}{c}X \\Y \\Z \\1\end{array}\right]$$ 
$$\begin{aligned}u & =\frac{m_{11} X+m_{12} Y+m_{13} Z+m_{14}}{m_{31} X+m_{32} Y+m_{33} Z+m_{34}} \\v & =\frac{m_{21} X+m_{22} Y+m_{23} Z+m_{24}}{m_{31} X+m_{32} Y+m_{33} Z+m_{34}}\end{aligned}$$ 
## Linearisierung 
$$\begin{array}{l}u \cdot\left(m_{31} X+m_{32} Y+m_{33} Z+m_{34}\right)=m_{11} X+m_{12} Y+m_{13} Z+m_{14} \\v \cdot\left(m_{31} X+m_{32} Y+m_{33} Z+m_{34}\right)=m_{21} X+m_{22} Y+m_{23} Z+m_{24}\end{array}$$ 
### $A$ (2N x 12) 
$$A=\left[\begin{array}{cccccccccccc}X_{1} & Y_{1} & Z_{1} & 1 & 0 & 0 & 0 & 0 & -u_{1} X_{1} & -u_{1} Y_{1} & -u_{1} Z_{1} & -u_{1} \\0 & 0 & 0 & 0 & X_{1} & Y_{1} & Z_{1} & 1 & -v_{1} X_{1} & -v_{1} Y_{1} & -v_{1} Z_{1} & -v_{1} \\X_{2} & Y_{2} & Z_{2} & 1 & 0 & 0 & 0 & 0 & -u_{2} X_{2} & -u_{2} Y_{2} & -u_{2} Z_{2} & -u_{2} \\0 & 0 & 0 & 0 & X_{2} & Y_{2} & Z_{2} & 1 & -v_{2} X_{2} & -v_{2} Y_{2} & -v_{2} Z_{2} & -v_{2} \\\vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots & \vdots \\X_{N} & Y_{N} & Z_{N} & 1 & 0 & 0 & 0 & 0 & -u_{N} X_{N} & -u_{N} Y_{N} & -u_{N} Z_{N} & -u_{N} \\0 & 0 & 0 & 0 & X_{N} & Y_{N} & Z_{N} & 1 & -v_{N} X_{N} & -v_{N} Y_{N} & -v_{N} Z_{N} & -v_{N}\end{array}\right]$$ 
### $x$ (12 x 1) 

$$\boldsymbol{x}=\left[\begin{array}{l}m_{11} \\m_{12} \\m_{13} \\m_{14} \\m_{21} \\m_{22} \\m_{23} \\m_{24} \\m_{31} \\m_{32} \\m_{33} \\m_{34}\end{array}\right]$$ 
### $A \cdot x=0$ 

## SVD 
- Die Eigenschaften von SVD: dass die Lösung x **die letzte Spalte von V** ist (die Spalte, die dem **kleinsten singulären Wert** entspricht). 
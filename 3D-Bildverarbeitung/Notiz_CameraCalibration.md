# Unterschied zwischen WKS und KKS 

| Eigenschaft |         Weltkoordinatensystem (WKS)          |                 Kamerakoordinatensystem (KKS)                  |
| :---------: | :------------------------------------------: | :------------------------------------------------------------: |
| Definition  | Globales, festes Koordinatensystem der Szene |           Lokales, kamerabezogenes Koordinatensystem           |
|  Ursprung   |       Beliebig in der Szene festgelegt       | Im optischen Zentrum der Kamera (dem Loch im Lochkameramodell) |


# Mit 1 Kamera 
## Pinhole camera 
### Definition 
Es besteht aus einem kleinen Loch (der „Blende“) auf der Vorderseite und einer Bildebene auf der Rückseite. Licht von einem Punkt in der Szene tritt durch das Loch und trifft auf die Bildebene, wodurch ein Bild entsteht. Das Lochkameramodell basiert auf dem Prinzip der **zentralen Projektion**, bei der alle Lichtstrahlen durch einen einzigen Punkt (das Loch) verlaufen. 

### Projektive Transformation 
<img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-26_20-07-49.png?raw=" width="60%" /> 

#### Definition 
beschreibt, wie Punkte im dreidimensionalen Raum auf eine zweidimensionale Bildebene projiziert werden. 

#### Abweichungen 
<img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-26_20-09-56.png?raw=" width="60%" /> 
1. Offset (Versatz der Bildmitte): Im idealen Lochkameramodell wird angenommen, dass die optische Achse der Kamera genau durch den Mittelpunkt der Bildebene verläuft. In der Realität ist dies jedoch oft nicht der Fall. Dies führt zu einem Versatz der Bildmitte, der durch die Parameter $c_x, c_y$ beschrieben wird. 
2. Pixel dimensions (Pixelgröße): Im idealen Modell wird angenommen, dass die Pixel auf der Bildebene quadratisch sind und eine einheitliche Größe haben. In der Realität können Pixel jedoch rechteckig sein und unterschiedliche Abmessungen in horizontaler und vertikaler Richtung aufweisen. Dies wird durch die skalierten Brennweiten $f_x$​ und $f_y$​ berücksichtigt. 
3. Skewness (Verzerrung durch Schiefstellung): Im idealen Modell wird angenommen, dass die Pixelachsen (horizontal und vertikal) perfekt orthogonal zueinander stehen. In der Realität kann es jedoch vorkommen, dass die Achsen nicht genau rechtwinklig zueinander ausgerichtet sind, z.B. aufgrund von Fertigungsungenauigkeiten im Kamerasensor. Dies wird durch den Schiefheitsparameter $\alpha$ (auch "Skew" genannt) berücksichtigt. Der Schiefheitsparameter beschreibt, wie stark die Pixelachsen von der Orthogonalität abweichen. 

#### Lösung 
<img src="https://raw.githubusercontent.com/xiaomeng-huang-study/images_3DBV/refs/heads/main/Scrennshot_2025-01-26_20-11-07.png?raw=" width="50%" /> 


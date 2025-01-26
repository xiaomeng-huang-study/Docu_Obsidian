# Mit 1 Kamera 
## Pinhole camera 
### Definition 
Es besteht aus einem kleinen Loch (der „Blende“) auf der Vorderseite und einer Bildebene auf der Rückseite. Licht von einem Punkt in der Szene tritt durch das Loch und trifft auf die Bildebene, wodurch ein Bild entsteht. Das Lochkameramodell basiert auf dem Prinzip der **zentralen Projektion**, bei der alle Lichtstrahlen durch einen einzigen Punkt (das Loch) verlaufen. 
### Projektive Transformation 
#### Definition 
beschreibt, wie Punkte im dreidimensionalen Raum auf eine zweidimensionale Bildebene projiziert werden. 
#### Abweichungen 
1. Off set (Versatz der Bildmitte): Im idealen Lochkameramodell wird angenommen, dass die optische Achse der Kamera genau durch den Mittelpunkt der Bildebene verläuft. 
2. Pixel dimensions (Pixelgröße): Im idealen Modell wird angenommen, dass die Pixel auf der Bildebene quadratisch sind und eine einheitliche Größe haben. In der Realität können Pixel jedoch rechteckig sein und unterschiedliche Abmessungen in horizontaler und vertikaler Richtung aufweisen. Dies wird durch die skalierten Brennweiten $f_x$​ und $f_y$​ berücksichtigt. 
3. Skewness (Verzerrung durch Schiefstellung): Im idealen Modell wird angenommen, dass die Pixelachsen (horizontal und vertikal) perfekt orthogonal zueinander stehen. In der Realität kann es jedoch vorkommen, dass die Achsen nicht genau rechtwinklig zueinander ausgerichtet sind, z.B. aufgrund von Fertigungsungenauigkeiten im Kamerasensor. Dies wird durch den Schiefheitsparameter $\alpha$ (auch "Skew" genannt) berücksichtigt. Der Schiefheitsparameter beschreibt, wie stark die Pixelachsen von der Orthogonalität abweichen. 



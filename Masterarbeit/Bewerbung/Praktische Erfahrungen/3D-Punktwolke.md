# SMART 
## Spezifisch 
Ziel des Projekts ist es, in einer **Abfolge von 3D-Punktwolken** **bewegte Objekte** zu erkennen. 
Dabei wurden verschiedene Punktwolken **zeitlich miteinander verglichen**, um zu analysieren, welche Punkte sich **signifikant verändert oder bewegt** haben. 

## (Messbar) 


## Attraktiv 
- Autonomes Fahren 
- Sicherheits- und Überwachungssysteme 
- Roboter-Navigation in dynamischen Umgebungen 

## Realistisch 
- Die Umsetzung erfolgte in **Python**, mit Hilfe Bibliotheken wie **Open3D, scikit-learn**. 

## Terminiert 
- allein 
- "3D-Bildverarbeitung" 
- 3 Monaten 


# Fragen 
## Funktionsweise 
- Zuerst habe ich die Punktwolken mit **ICP (Iterative Closest Point)** registriert, um eine globale Referenz herzustellen. 
- Dann habe ich die **Differenzen der Punkte analysiert**. 
- Danach habe ich **DBSCAN** verwendet, um die Punkte mit signifikanter Bewegung in verschiedene **Cluster** zu **klassifizieren** und die sich bewegenden Objekte weiter auszuwählen. 

## DBSCAN 
- keine feste Anzahl von Clustern, und DBSCAN basiert auf Dichte. 
- gegen Rauschen 

## Visualisierung 
die Ergebnisse wurden mit **Open3D** visualisiert. 
Ich habe die bewegten Punkte **farblich** hervorgehoben, sodass man die Bewegungsrichtung und -intensität leicht erkennen konnte. 

## Herausforderungen 
### Rauschen in den Daten 
Schwellenwerte anzupassen 


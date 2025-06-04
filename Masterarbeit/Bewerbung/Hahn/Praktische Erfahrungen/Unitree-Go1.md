# SMART 
## Spezifisch 
Das Ziel ist, dass der Roboter **Unitree Go1** ein **rotes Objekt (ein Würfel)** mit seiner **integrierten Kamera** erkennt und diesem folgt. 

## Messbar 
Die Zuverlässigkeit des Systems wurde daran gemessen, wie **gut** der Roboter einem Objekt folgen konnte- besonders in Abhängigkeit von der **ursprünglichen Entfernung** zwischen Roboter und Objekt.
Wenn das **Umgebungslicht** angemessen **gesteuert** werden kann, kann der Roboter die meisten Aufgaben **erledigen**. 

## Attraktiv 
Das Projekt ist besonders **relevant** für Anwendungen in der **Such- und Rettungsrobotik**.  
Gleichzeitig sind **Bildverarbeitung** und **Regelungstechnik** Schlüsselfelder für viele **automatisierte Systeme** in der Industrie und Robotik. 

## Realistisch 
Die Umsetzung erfolgte mit **C++ und OpenCV** zur Bildverarbeitung. 
Für die Steuerung und Kommunikation wurde **ROS (Robot Operating System)** eingesetzt. 
Auf dem Roboter wurde ein **Jetson Nano** integriert, was eine **ausreichend schnelle Verarbeitung** der Bilddaten ermöglichte. 

## Terminiert 
- 3 Personen 
- 4 Monaten 


# Fragen 
## Farbverfolgung 
Wir haben mit OpenCV gearbeitet. Zuerst haben wir das Kamerabild in den **HSV-Farbraum** umgewandelt, da dieser robuster gegenüber Lichtveränderungen ist.  
Dann haben wir eine **Farbmaske für Rot** definiert, Konturen erkannt und das Objekt zentriert.  
Die Position wurde anschließend an den PID-Regler weitergegeben, um Bewegungsbefehle an den Roboter zu übermitteln. 

## PID-Regler 

## Herausforderungen 
### Lichtverhältnissen 
bei **starkem Schatten oder Reflexion** 
- ein breiteres HSV-Spektrum, Toleranzbereich 
- **Filter** 


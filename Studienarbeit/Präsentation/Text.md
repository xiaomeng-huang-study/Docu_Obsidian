## Programm Colorfollower 
- Wie Thilo beschrieben hat, haben wir eine Beispielapplikation implementiert. Der Name ist ColorFollower. 
- Ich würde mit der Erklärung anfangen. 

## Übersicht_1 
- Zuerst möchte ich euch einen allgemeinen Überblick geben. 

- Das Slide zeigt eine ==Ansicht aus der Vogelperspektive==, nämlich Draufsicht. 
- ==Wenn== dieses Programm die Kontrolle über die Bewegungen des Roboters ==übernimmt==, werden 2 Funktionalitäten realisiert. 
	- Ich werde mit 2 Video als Beispiele zeigen, was dieses Programm machen kann. 
	- Eine davon ist, die Richtung zu kontrollieren. ... Video ... Das heißt, der Roboter kann sich immer nach dem Objekt orientieren. 
	- die 2. Funktionalität ist, den Abstand zu dem Objekt zu kontrollieren. ... Video ... Das heißt, der Roboter kann den Abstand zum Objekt halten. 

## Übersicht_2 
- Hier wird ein vereinfachtes Ablaufdiagramm des Systems gezeigt. Dies ist ein typischer geschlossener Regelkreis. 

- In dem linken Teil müssen wir Ziele eingeben, z. B. den Abstand, der zwischen dem Objekt und dem Roboter eingehalten werden soll. 
- In dem rechten Teil können wir die Bewegung des Roboters als Ausgabe sehen. 
- Über die am Roboter montierte Kamera werden Bilddaten erfasst, verarbeitet und für die Bewegungssteuerung verwendet. 
- In Bezug auf die vorgegebenen Ziele und die aktuelle Situation wird die Bewegungskontrolle dem Roboter Bewegungsbefehle geben. 

## ColorFollower Bildverarbeitung 
### 1. Teil 
- Für die Bildverarbeitung habe ich hier einen Ausschnitt aus dem gesamten Prozess übernommen. 

- Über die Kamera auf dem Roboter kann man ein rektifiziertes Bild bekommen. 
- Mit Hilfe von Technologien wie OpenCV kann das Programm nach dem HSV-Modell Farbe erkennen. 

- HSV ist üblich für Farbe-Erkennung benutzt. 
	- H: Hue, auf Deutsch Farbton. Es wird in Grad gemessen und kann einen Wert von 0 bis 360 Grad haben. Rot hat z.B. 0 Grad. 
	- S: Saturation, auf Deutsch Sättigung. Es repräsentiert, wie bunt eine Farbe ist, und wird in Prozent gemessen. 
	- V: Value, auf Deutsch, Wert. Es repräsentiert, wie hell eine Farbe ist und wird in Prozent gemessen. 
- Mit Schwellenwerten auf diesen 3 Dimensionen kann man eine Toleranz für die Erkennung einstellen. 
- Das Programm bietet auch Visualisierungsoptionen. Hier wird ein Bild im HSV-Farbmodus gezeigt. 

### 2. Teil 
- Es ist einfacher zu verstehen, wenn wir das Bild im Binärfarbmodus betrachten. Alle passenden Pixel werden als wahr markiert, d.h. der weiße Teil des Bildes, und der Rest wird als falsch markiert, d.h. der schwarze Teil des Bildes. 
- Das Programm verbindet dann alle Pixel, die den Bedingungen entsprechen, und zeichnet einen Bounding Box, der sie einschließt. In diesem Beispiel ist das grüne Kästchen Bounding Box. 
- Als Ausgabe kann das Programm die Höhe und die horizontale Position des Objekts abliefern, die für spätere Schritten nützlich sind. 
- Vor der Ausgabe kann man Filter einsetzen, um die Störung zu minimieren. 
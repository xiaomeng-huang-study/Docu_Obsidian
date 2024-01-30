## Programm Colorfollower 
- Wie Thilo beschrieben hat, haben wir eine Beispielapplikation implementiert. Der Name ist ColorFollower. 
- Ich würde mit der Erklärung anfangen. 

## Übersicht_1 
- Zuerst möchte ich euch einen allgemeinen Überblick geben. 

- Das Slide zeigt eine ==Ansicht aus der Vogelperspektive==, nämlich Draufsicht. 
- ==Wenn== dieses Programm die Kontrolle über die Bewegungen des Roboters ==übernimmt==, werden 2 Funktionalitäten realisiert. 
	- Ich werde ==mit 2 Video als Beispiele== zeigen, was dieses Programm machen kann. 
	- Eine davon ist, die Richtung zu kontrollieren. ... Video ... Das heißt, der Roboter kann sich immer nach dem Objekt orientieren. 
	- die 2. Funktionalität ist, den Abstand zu dem Objekt zu kontrollieren. ... Video ... Das heißt, der Roboter kann den Abstand zum Objekt halten. 




- Ich werde ==mit einem Beispiel== zeigen, was dieses Programm machen kann. 
- Schauen Sie bitte die linke Seite an. 

- Der Roboter ist jetzt nach oben ausgerichtet.
- Dieses rote Objekt ist das Ziel, das der Roboter verfolgen soll. 
- Nach den ==grünen gepunkteten Linien und den Pfeil== kann man erkennen, befindet sich das aktuelle Objekt vor dem Roboter auf der linken Seite. 

- ==Wenn== dieses Programm die Kontrolle über die Bewegungen des Roboters ==übernimmt==, können Sie die Ergebnisse im rechten Teil sehen. Der Roboter hat seine Richtung und seinen Abstand zum Ziel angepasst, um dieses Objekt zu verfolgen. 
- Wenn man diese Bewegung ==zerlegt==, kann man sich vorstellen, dass der Roboter sich auf der Stelle dreht, um sich zu orientieren, und sich hin und her bewegt, um den Abstand zum Objekt zu halten. 

## Übersicht_2 
- Hier wird ein vereinfachtes Ablaufdiagramm des Systems gezeigt. Dies ist ein typischer geschlossener Regelkreis. 

- In dem linken Teil müssen wir Ziele eingeben, z. B. den Abstand, der zwischen dem Objekt und dem Roboter eingehalten werden soll. 
- In dem rechten Teil können wir die Bewegung des Roboters als Ausgabe sehen. 
- Über die am Roboter montierte Kamera werden Bilddaten erfasst, verarbeitet und für die Bewegungssteuerung verwendet. 
- ==In Bezug auf== die vorgegebenen Ziele und die aktuelle Situation wird die Bewegungskontrolle dem Roboter Bewegungsbefehle geben. 
- Dieser Regelkreis arbeitet im Zyklus, d.h. er wird dynamisch dem Objekt verfolgen. 

## ColorFollower Bildverarbeitung 
- Für die Bildverarbeitung wird im oberen Teil ein vereinfachtes Ablaufdiagramm gezeigt. 

- Mit Hilfe von Technologien wie OpenCV ist es möglich, ein Frame zu erfassen, das mehrere Objekte enthält. 

- Für die Farbe-Erkennung haben wir HSV-Algorithmus benutzt. 
	- H: ==Hue, auf Deutsch Farbton==. Es wird in Grad gemessen und kann einen Wert von 0 bis 360 Grad haben. Rot hat z.B. 0 Grad. 
	- S: Saturation, auf Deutsch Sättigung. Es repräsentiert, wie bunt eine Farbe ist, und wird in Prozent gemessen. 
	- V: Value, auf Deutsch, Wert. Es repräsentiert, wie hell eine Farbe ist und wird in Prozent gemessen. 
- Wenn man eine Toleranz für die Erkennung einstellt, können alle Pixel mit Farbe Rot ausgewählt. Dann wird ein Kästchen, das alle möglichen Pixel beinhaltet, gemalt, nämlich Bounding Box. Wie Sie in diesem Bild sehen können, wird ein grünes Kästchen verwendet, um das erkannte rote Objekt zu markieren. 

- Wie Sie auf diesem vergrößerten Bild sehen können, sind auch kleine grüne Kästchen in der Position der Hand abgebildet. Die werden als Störung angesehen. Um Störungen bis zu einem gewissen Grad zu vermeiden, haben wir vor der Ausgabe eine Prüfung der Bounding Box hinzugefügt. Nur wenn diese Bedingungen erfüllt sind, können die Informationen ausgegeben werden, die für spätere Schritte nützlich sind. Z.B. die horizontale Position von dem Objekt. 
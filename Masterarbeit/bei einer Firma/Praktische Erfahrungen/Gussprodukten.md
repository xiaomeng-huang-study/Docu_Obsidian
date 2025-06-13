# SMART 
## Spezifisch 
In diesem Projekt habe ich ein neuronales Netz entwickelt, um Gussprodukte anhand von Bilddaten in zwei Klassen zu unterteilen: **"gut"** oder **"defekt"**.  
Die Bilder waren RGB-Bilder und stammen aus einem öffentlichen Datensatz auf **Kaggle**. 

## Messbar 
Die Modellleistung wurde mit **Precision, Recall** und der **Confusion-Matrix** bewertet. So konnte man gut erkennen, wie zuverlässig das Modell arbeitet. 

## Attraktiv 
Solche Systeme können die **Effizienz in der Produktion stark erhöhen**. Ich habe auf der Hannover Messe gesehen, dass z. B. Amazon ähnliche Techniken bereits erfolgreich in Fertigungsprozesse integriert. 
Deshalb sehe ich hier ein hohes Praxispotenzial. 

## Realistisch 
Ich habe das Modell in **Python mit PyTorch** programmiert. Für das Training habe ich vor allem **Google Colab** genutzt, aber auch auf leistungsstarke Rechner der Hochschule zurückgegriffen.  
Der Datensatz bestand aus etwa **5000 Bildern** – die Datenmenge war gut handhabbar, und das Training hat in akzeptabler Zeit funktioniert. 

## Terminiert 
Das Projekt habe ich **eigenständig** durchgeführt. Die gesamte Laufzeit betrug etwa **drei Monate**. 


# Fragen 
## Architektur 
Ich habe mich für **Transfer Learning** entschieden und dabei **ResNet18** und **ResNet50** verwendet.  
Diese Architekturen basieren auf dem **Residual-Netzwerk**, das 2015 bei ImageNet eingeführt wurde und dort als erstes Modell die menschliche Genauigkeit übertroffen hat. 

Der Grund für diese Wahl war, dass ResNet **sehr leistungsstark**, **gut dokumentiert** und auch für mein Projekt geeignet ist, weil ich nur etwa 5000 Bilder hatte.  

## Overfitting 
- Datenaugmentation z. B. durch Drehen und Spiegeln der Bilder. 
- Dropout-Schichten eingefügt 

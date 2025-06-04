In diesem Projekt habe ich mit zwei Kommilitonen eine Mensch-Roboter-Kollaboration aufgebaut. 

# SMART 
## Spezifisch 
Ziel ist, dass der Roboter eine Leiterplatte aus dem Lager holt, sie während des Lötvorgangs hält und danach auf ein Förderband legt.  
Der Mensch ist für die Platzierung der Platine, Lötarbeit, Qualitätskontrolle zuständig. 


## (Messbar) 
Das wichtigste Ziel ist, dass der gesamte Prozess stabil funktioniert. 
Dabei steht die Sicherheit im Vordergrund. 


## Attraktiv: Warum war das Projekt wichtig oder sinnvoll? 
Dieses Projekt ist sehr praxisrelevant für die Industrie. Menschen können komplexe Aufgaben wie Löten und Qualitätskontrolle besser durchführen, während der Roboter einfache, aber wiederholende Aufgaben übernimmt. Das spart Zeit und erhöht die Effizienz in der Produktion. 


## Realistisch 
Im Labor wird ein KUKA iiwa angeboten. 
Für die Aufgabe haben wir auch einen eigenen Greifer entworfen und mit dem 3D-Drucker produziert – so konnte der Roboter die Leiterplatte sicher greifen. 


## Terminiert 
Das Projekt ist ein Teil vom Kurs "Mensch-Roboter-Kollaboration" und läuft über drei Monate. 


# mögliche Fragen 
## Herausforderungen 
Eine große Herausforderung ist die genaue Definition der Flugbahn eines Roboters. Wir müssen die Bewegungen des Roboters so programmieren, dass sie sowohl sicher als auch vorhersehbar sind, ohne den Menschen zu gefährden. 

## Sicherheit 
Sicherheit ist ein zentraler Aspekt in unserem Projekt. Wir haben zuerst mögliche Gefahren analysiert und in drei Kategorien eingeteilt: 
1. **Gefahren bei normaler Verwendung**, 
2. **Gefahren bei vorhersehbarer Fehlanwendung**, 
3. und wir haben uns dabei an die Norm **DIN EN ISO 10218** orientiert. 
Darauf basierend haben wir Maßnahmen aus drei Perspektiven abgeleitet: 
- **Konstruktiv:** physische Barrieren 
- **Softwareseitig:** Not-Halt-Schalter 
- **Organisatorisch:** Schutzbrille 
Außerdem haben wir nach dem Standard **ISO/TS 15066** die **Kraft- und Leistung des Roboters** eingeschränkt. 

## Rolle 
Roboterprogrammierung 

## Greifer 
- Vorlage von dem vorhandenen Greifer übernommen
- Autodesk Fusion 360 

## Programmierung 
- mit Sunrise.OS  
- Java object-oriented 

### object-oriented 
- Kapselung: Daten und Funktionen werden in einer Klasse zusammengefasst. 
- Vererbung: Eigenschaften und Methoden einer anderen Klasse übernehmen $\Rightarrow$ spart Wiederholungen 
- Polymorphie: Eine Methode kann unterschiedliche Implementierungen haben $\Rightarrow$ Schnittstelle 
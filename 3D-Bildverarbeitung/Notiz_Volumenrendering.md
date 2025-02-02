- IVR aufwendiger als DVR, wenn die Position der Kamera sich verändert 

Ray neu berechnen, wenn sich die Kamera bewegt: 
Eingangsdaten: Datensatz, sample rate, lichtpose, Transferfunktion 


# Unterschiede zwischen Direkten und Indirekten Volumenrendering 

|**Kriterium**|**Direktes Volumenrendering**|**Indirektes Volumenrendering**|
|---|---|---|
|**Darstellung**|Gesamtes Volumen inkl. Transparenz|Nur explizite Oberflächen|
|**Berechnungsaufwand**|Höher|Niedriger|
|**Datenverarbeitung**|Ohne vorherige Oberflächenextraktion|Mit vorheriger Oberflächenextraktion|
|**Innere Strukturen**|Sichtbar|Nicht sichtbar|
|**Beispiele**|CT/MRT-Scans, Flüssigkeitssimulation|3D-Druck, Oberflächenmodellierung|


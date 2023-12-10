#### 1\. Nachvollziehen der Schritte im Jupyter Notebook zum ResNet

##### 1\.1 Analysieren sie die Ergebnisse für die Modelle 1 und 2.

* 1 Modell: max=72% und großes Overfitting
* 2 Modell (mit learning rate Veränderung): max zwar 86%, also deutlich besser als 1. Modell, dafür ist ab 11 Epochen keine Verbesserung mehr zu sehen, weil die Trainings-Genauigkeit 100% erreicht hat

##### 1\.2 Analysieren sie die Funktion: def ResidualBlocks(x, stack_n, filter_size)

* **Input:**
  * x: aktueller / bisherige Layer
  * stack_n: Anzahl residual Blöcke pro image size / feature map size
  * filter_size: Anzahl Kanäle am Anfang von Residual Blöcken
* **Output:**
  * bisherige Layer + Risidual Blöcke hinzugefügt

##### 1\.3 visualisieren sie das Verhalten der Funktion für 3 verschiedene Parametersätze, z. B. stack_n = 1, filter_size = 16 oder stack_n = 3, filter_size = 8

|  | n | 2n | 6n | 3n | filter_size |
|--|---|----|----|----|-------------|
|  | blocks per img size | layers per img size | layers in total | shortcuts / residual blocks in total | Anzahl Kanäle |
| **Beispiele** | 1<br />3 | 2<br />6 | 6<br />18 | 3<br />9 | 64 / 16<br />8 |

```mermaid
flowchart
test["Legend: &emsp; (/2 means strides=2)<br><br>convolutional layer, filter size"]
subgraph 1[n=1, filter_size=64]
direction TB
	s1[stem] --> c11[conv, 64<br>conv, 64] --> c12[img 32x32]
	s1 ---> c12
	c12 --> c13[conv, 128/2<br>conv, 128] --> c15[img 16x16]
	c12 --> c14[conv, 128/2] --> c15
	c15 --> c16[conv, 256/2<br>conv, 256] --> c18[img 8x8]
	c15 --> c17[conv, 256/2] --> c18
end

subgraph 2[n=1, filter_size=16]
direction TB
	s2[stem] --> c21[conv, 16<br>conv, 16] --> c22[img 32x32]
	s2 ---> c22
	c22 --> c23[conv, 32/2<br>conv, 32] --> c25[img 16x16]
	c22 --> c24[conv, 32/2] --> c25
	c25 --> c26[conv, 64/2<br>conv, 64] --> c28[img 8x8]
	c25 --> c27[conv, 64/2] --> c28
end

subgraph 3[n=3, filter_size=8]
direction TB
	s3[stem] --> c311[conv, 8<br>conv, 8]
	subgraph 31[layer_group=0]
        c311 --> c321[img 32x32] -->
        c312[conv, 8<br>conv, 8] --> c322[img 32x32] --> c313[conv, 8<br>conv, 8]
        c321 ---> c322
	end
	s3 ---> c321
	c313 --> c32
	c322 --->	c32[img 32x32]
	
	
	c32 --> c331[conv, 16/2<br>conv, 16] --> c351[img 16x16] --> c332[conv, 16<br>conv, 16] --> c352[img 16x16] --> c333[conv, 16<br>conv, 16] --> c35[img 16x16]
	c32 --> c34[conv, 16/2] -->  c351 --> c352 ---> c35
	
	c35 --> c361[conv, 32/2<br>conv, 32] --> c381[img 8x8] --> c362[conv, 32<br>conv, 32] --> c382[img 8x8] --> c363[conv, 32<br>conv, 32] --> c38[img 8x8]
	c35 --> c37[conv, 32/2] --> c381 --> c382 ---> c38
end
```

#### 2\. Erzeugen sie ein 3. Modell was auf eine Accuracy auf dem Test-Set von mehr als 89% kommt.

```
Datei: 92_Training_ResNet.ipynb
```

<img src="image16692041019600.png" width=70% />

##### 2.1 Änderungen

- Hinzufügen von Conv-Layern beim Stem Network, am Beginn der Architektur, die Sprünge waren (32, 32, 3) auf (32, 32, 64) jetzt: (32, 32, 3) -> (32, 32, 16) -> (32, 32, 32) -> (32, 32, 64)
- Einfügen einer Augmentation, Parameter:

  - width_shift_range  = 0.1

  - height_shift_range = 0.1

  - horizontal_flip        = ture

  - rotation_range       = 10

  - zoom_range           = [ 0.9, 1.2 ]

  - shear_range           = 5
- Scheduler umkonfigurieren
  - Learning rate wird um Faktor 10 verkleinert (von 0,1 -> 0,01 -> 0,001) bei den Epochen 65 und 88.

##### 2.2 Analyse

- Bei der ersten Änderung der Learningrate kommen wir in den ersten 100 Epochen auf 91% [Epoche 65]
- Die zweite Änderung macht augenscheinlich keinen großen Einfluss [Epoche 88], könnte durch weitere feine Justierung noch optimiert werden
- Nach den ersten 100 Epochen schaffen wir nicht ganz die 92%, die Besten Ergebnisse sind: bei Epoche 83 und 94 mit einem Wert von 91,93% (Validierungswert)
- Was auffällt, wir haben bei den ersten 100 Epochen eine Trainingaccuracy von annähernd 100%
- zwischen 100 und 200 Epochen pendelt es sich bei 92% ein, was die val_accuracy angeht.
- Das Beste Ergebnis ist zwischen 100 und 200 Epochen mit 92,19%
## statische Polymorphie
- Überladen
	- Funktion überladen
	- Operator überladen
- redefining

## dynamische Polymorphie
- virtuelle Funktionen (virtual function)
	- überschreiben (override)

- `virtual` + `=0` $\Rightarrow$ abstrakte Klasse
	- Instanzierung verboten
	- Unterklasse muss alle virtuelle Methode überschreiben

- außerhalb von Konstruktor sollen mit `virtual` beschrieben werden.
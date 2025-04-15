# Speicherarchitektur 
Unterschied: getrennt 

```C++
/*Load working page*/ 
int i = 3; // globale initialisierte Var. Parameter // i in Arbeitsseite in RAM; 3 in Referenzseite in Flash ROM 
/*Define Messwerte*/ 
int j; globale nicht-initialisierte Var. // Messwerte // in RAM 

void main(){
	j = i;
	i = 5;
}
```

```C++
int a[50]; 
int b = 5; 

void foo(){
	int c[40];
}

void main(){
	int d; 
	int e = 7;
	d = b; 

	foo();

	myclass = new f;
	free();
}
```
# Speicherabbild 
## Beispiel A2L Datei 
- Param_ROM: Parameter 
- Code: 
- Signals: Messwerte 

## Warum nur 3 Bereiche 
denn der Offset zwischen Referenzseite und Arbeitsseite ist fest 
Deswegen ist nur die Speicherung von Referenzseite und Offset erforderlich 

# XCP Download / Upload 
- Kann nur aus Master gestartet werden. 

## Nachteile 
- synchron zur Modellausführung: idealerweise -> Funktion ausführen, dann Ergebnis schicken; Funktion ausführen, dann Ergebnis schicken; .... 


# Adressen in A2L Datei 
`Linker.map` ist für die Adresse zuständig 
- Untere Klassen 
	```python
	class derivedClass_Name(baseClass_Name):
		...
	```
	- Konstruktor 
		- Falls untere Klasse keine eigenen Konstruktor hat 
			- Konstruktor von <font color = "red">oberer</font> Klasse wird aufgerufen 
		- Falls untere Klasse eigenen Konstruktor hat
			- Konstruktor von <font color = "red">unterer</font> Klasse wird aufgerufen 
			- kann Konstruktor von oberer Klasse benutzen 
				- mit `super().__init__(para1, ...)` $\Rightarrow$ Rückgabe: obere Klasse 


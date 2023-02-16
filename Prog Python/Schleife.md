## FOR 
- FOR mit `range()` 
	- `range_(start, stop, step)` 
		- start einschließlich 
		- stop <font color = "red">nicht</font> einschließlich 
		- step default 1
	```python
	for num in range(1, 10, 2):
	```
- FOR mit Dic 
	```python
	for temp_key, temp_value in dic.items():
	```

## WHILE 
```python
while Bedingung : 
```

- komplettes Beispiel 
	```python
	arr = ["A", "B", "C", "D"]
	
	for tem_Elem in arr:
	    print(tem_Elem)
	    
	for i in range(len(arr)):
	    print(arr[i])
	
	i = 0
	while i < len(arr):
	    print(arr[i])
	    i += 1
	```
	- AVG berechnen 
		```python
		# Array erzeugen
		Zahlen = []
		Eingabe = input("Bitte geben Sie eine Zahl ein: \n")
		while 'q' != Eingabe:
			Zahlen.append(float(Eingabe))
			Eingabe = input("Bitte geben Sie eine Zahl ein: \n")
		
		# Summe berechnen
		Summe:float
		Summe = 0
		for temp_Elem in Zahlen:
			Summe += temp_Elem
		
		# AVG berechnen
		if 0 != len(Zahlen):
			print("AVG: " + str(Summe/len(Zahlen)))
		else:
			print("AVG kann nicht berechnet werden, da Nenner 0 ist")
			
		print(Zahlen)
		```
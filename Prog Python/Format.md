- mit automatischer Hochzählung 
	```python
	Elem1 = 'D'
	Elem2 = 'E'
	content = """
	A,B,C,{0},{1}
	    #{0} durch Elem1 ersetzt, {1} durch Elem2 ersetzt
	""".format(Elem1, Elem2)
	print(content)
	```
- mit Parameterübergabe 
	```python
	Elem1 = 'D'
	Elem2 = 'E'
	content = """
	A,B,C,{current_Elem1},{current_Elem2}
	""".format(current_Elem2 = Elem2,
	           current_Elem1 = Elem1)
	print(content)
	```
- mit f-literal
	```python
	Elem1 = 'D'
	Elem2 = 'E'
	content = f"""
	A,B,C,{Elem1},{Elem2}
	"""
	print(content)
	```

- Beispiel 
	```python
	dic = {1: "A", 2: "B", 3: "C", 4: "D"}
	for temp_key, temp_value in dic.items():
	    print(f"{temp_key} zeigt auf {temp_value}")
	```

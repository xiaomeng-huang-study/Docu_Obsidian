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

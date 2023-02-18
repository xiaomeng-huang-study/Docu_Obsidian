- Erzeugen
	- 1.Methode
		```python
		myList = [..., ..., ...]
		```
	- 2.Methode: mit `list()` 
		```python
		myList = list([..., ..., ...])
		```

- Element $\Rightarrow$ Index 
	```python
	myList.index(...)
	```
	- in bestimmten Bereich 
		```python
		myList.index(..., start_Index, stop_Index)
		```
		- `start` inklusiv, `stop` nicht inklusiv 
- Index $\Rightarrow$ Element 
	- Bereich von Index 
		- positive Index: $0 \rightarrow N-1$ 
			```python
			myList[0]
			```
		- negative Index: $-N \rightarrow -1$ 
			```python
			myList[-1]
				#das letzte Element
			```

- SORT und SORTED
	- `arr.sort()` $\Rightarrow$ arr wird verändert 
	- `arrB = sorted(arrA)` $\Rightarrow$ arrA wird <font color = "red">nicht</font> verändert, arrB ist neu 
	- absteigend 
		- `arr.sort(reverse = True)` 
		- `arrB = sorted(arrA, reverse = True)` 
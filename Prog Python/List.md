- List Erzeugen
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

- slice notation
	- auf der <font color = "red">rechten</font> Seite $\Rightarrow$ <font color = "red">neue</font> List erzeugt 
		```python
		L2 = L1[start_Index: stop_Index: step]
		```
		- `start_Index` : default 0 
		- `step` : default 1 
		- `L2 = L1[0: 2: 1]` ![](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Prog_Python_List_slice_notation.png)  
	- auf der <font color = "red">linken</font> Seite $\Rightarrow$ <font color = "red">keine</font> neue List erzeugt 

- Element(e) hinzufügen 
	- `append()` 
		- als <font color = "red">ein</font> Element am Ende hinzufügen 
			- `L1.append(L2)`![](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Prog_Python_List_append_1.png) 
			- `L1.append(5)`![](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Prog_Python_List_append_02.png)  
	- `extend()` 
		- Elemente einer Liste an das Ende hinzufügen 
		- `L1.extend(L2)`![](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Prog_Python_List_extend.png)  
	- `insert()` 
		- ein Element an der angegebenen Position einfügen 
			- `L1.insert(1, 5)` ![](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Prog_Python_List_insert.png) 
 
- Element(e) löschen 
	- `remove()` : Value gewusst 
		- das <font color = "red">erste</font> Element mit dem angegebenen Wert entfernen 
	- `pop()` : Index gewusst 
		- das Element an der angegebenen Position entfernen 
		- Index nicht angegeben $\Rightarrow$ das letzte Element löschen 
	- mit slice notation Elemente löschen 
		- `L1[1: 3] = []` ![](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Prog_Python_List_l%C3%B6schen_mit_slice_notation.png)
	- `clear()` 
		-  alle Elemente aus der Liste entfernen 
			```python
			myList.clear()
			```
	- `del` 
		```python
		del myList
		```

- Element(e) ändern 
	- mit slice notation Elemente ersetzen 
		- `L1[1: 3] = L2` ![](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Prog_Python_List_ersetzen.png) 

- sortieren 
	- `myList.sort()` $\Rightarrow$ `myList` wird verändert 
	- `L2 = sorted(L1)` $\Rightarrow$ `L1` wird <font color = "red">nicht</font> verändert, `L2` ist neu 
		- `L2 = sorted(L1)` ![](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Prog_Python_List_sorted.png) 
	- absteigend 
		- `arr.sort(reverse = True)` 
		- `arrB = sorted(arrA, reverse = True)` 

- List Comprehensions 
	- Beispiel
		```python
		myList = [i*2 for i in range(1, 6)]
			#2,4,6,8,10
		```

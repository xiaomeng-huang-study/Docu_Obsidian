```python
dic = {
	key_A : value_A,   #mit komma zu trennen
	key_B : value_B
}
```
- Key kann auch tuple sein 
	- `(subkey_A_1,subkeyA_2)` 
- Key darf <font color = "red">nicht</font> List oder Dictionary sein
- Methoden dazu 
	- prüfen, ob key in dic 
		- `key_C in dic` 
			- falls in: true 
			- falls nicht in: false 
	- hinzufügen/ überschreiben 
		- `dic[key_C] = "..."` 
	- löschen key 
		- `del dic[key_C]` 
	- Länge 
		- `len(dic)` 
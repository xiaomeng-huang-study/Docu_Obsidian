| Befehl | Einfluss auf Datentyp     |
| :-----: | :-------------: |
| \&     | \* hinzufügen |
| \*     | \* entfernen  |

- Zeiger definieren und initialisieren
	```c++
	int *p = NULL;
	```
	- Typen
		- Typ von <u>Variable</u>: VariableName einhalten $\rightarrow$ die übrige
			- z.B. "p" einhalten $\rightarrow$ Typ von p ist int \*
		- Typ von Daten, auf die die Variable <u>zeigt</u> : \* und VariableName einhalten $\rightarrow$ die übrige  
			- z.B. "\*p" einhalten $\rightarrow$ int
- 指向类型决定
	- 取值宽度
	- +1跨度
	- ![|675](https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/cpp_%E5%8F%96%E5%80%BC%E5%AE%BD%E5%BA%A6.jpg)
		- z.B. \*p1 $\rightarrow$ 4Byte(01020304)
		- z.B. p1+1 $\rightarrow$ 4Byte überspringen
		- komplettes Beispiel
			- 0203 lesen
				- 跨度=1Byte $\rightarrow$ `char *p = (char*)&num` 
				- 宽度=2Byte $\rightarrow$ `*((short*)(p+1))` 
- array\[i] = \*(array+i)

## char_Array
	```c++
	char str[6] = "Hello";
	```
- intern
| H   | e   | l   | l   | o   | \0  |
| --- | --- | --- | --- | --- | --- |
- Größe: `sizeof(str)` = 6

## Zeiger auf String
	```c++
	char *str = "Hello";
	```
- Typ von str: char \* $\rightarrow$ `sizeof(str)` = 4
- 




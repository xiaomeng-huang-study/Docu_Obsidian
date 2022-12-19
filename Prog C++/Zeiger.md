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

## String
### 1)char_Array als String
```c++
char str[6] = "Hello";
```
- intern
| H   | e   | l   | l   | o   | \0  |
| --- | --- | --- | --- | --- | --- |
- Größe: `sizeof(str)` = 6
- Beispiel
	```c++
	    char str[6] = "Hello";
	    printf("%s",str);
	    cout<<str<<endl;
	```

### 2)Zeiger auf String
```c++
char *str = "Hello";
```
- <font color = "red">String in Datensegment(文字常量区) gespeichert</font> : nur lesbar
- <font color = "red">str speichert nur die Adresse von erster char</font> 
- Typ von str: char \* $\rightarrow$ `sizeof(str)` = 4Byte 
- Beispiel
	```c++
	char *str = "Hello";
	printf("%s",str);
	cout<<str<<endl;
	```

### 3)Array of Pointer to String
```c++
char *arr[4]= {"Hello1","Hello2","Hello3","Hello4"};
```
- <font color = "red">ist ein Array</font> 
- <font color = "red">jedes Element ist ein Zeiger(Typ: char \*)</font> 
- `sizeof(arr)` = 4 $\cdot$ 4Byte 
- Beispiel
	```c++
	char *arr[4]= {"Hello1","Hello2","Hello3","Hello4"};
	printf("%s",arr[3]);    //keine * erforderlich
	```

## Array of Pointer
```c++
int a = 1, b = 2, c = 3, d = 4;
int *arr[4] = {&a,&b,&c,&d};
```
- <font color = "red">ist ein Array</font> 
- <font color = "red">jedes Element ist ein Zeiger(Typ: char \*)</font> 
- `sizeof(arr)` = 4 $\cdot$ 4Byte 
- Beispiel
	```c++
	int a = 1, b = 2, c = 3, d = 4;
	int *arr[4] = {&a,&b,&c,&d};
	printf("%d",*(arr[3]));     //* erforderlich
	cout<<*(arr[3])<<endl;
	```

## Pointer to Array
- Begriffe
	- Adresse von Array: \&arr 
		- (\&arr)+1 $\rightarrow$ gesamte Array überspringen 
	- Adresse von arr\[0\]: \&arr\[0\] 
		- (\&arr\[0\])+1 = arr $\rightarrow$ ein Element überspringen 
```c++
int arr[5] = {1,2,3,4,5};
int (*p)[5] = &arr;
```
- <font color="red">ist ein Zeiger</font> 
- <font color = "red">speichert Adresse von Array: &arr</font> 
- `sizeof(p)` = 4Byte 
- \*p == arr
- Beispiel
	```c++
	int arr[5] = {1,2,3,4,5};
	int (*p)[5] = &arr;
	printf("%d",(*p)[2]);
	cout<<(*p)[2]<<endl;
	```


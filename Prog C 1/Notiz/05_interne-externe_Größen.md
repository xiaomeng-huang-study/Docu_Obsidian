- **interne Größe** : innerhalb einer Funktion deklariert 
	- Speicherbereich: Stack
	- mit Attribut "static" $\Rightarrow$ überlebt nach Termination (nicht in Stack, in Datenspeicher) 
- **externe Größe** 
	- externe ==Variable/Konstante== : außerhalb jeder Funktionen deklariert
		- mit Attribut `extern`  $\Rightarrow$ hat dieser Modul Zugriff auf Variablen/ Konstanten aus anderen Modulen 
		- Beispiel
			```c++
			//fileA.cpp
			int i = 42; // declaration and definition
			
			//fileB.cpp
			extern int i;  // declaration only. same as i in FileA
			
			//fileC.cpp
			extern int i;  // declaration only. same as i in FileA
			
			//fileD.cpp
			int i = 43; // LNK2005! 'i' already has a definition.
			extern int i = 43; // same error (extern is ignored on definitions)
			```
	- ==Funktionen== 
		- mit <u>Deklaration bzw. Prototyp</u> in betreffenden Modulen $\Rightarrow$ hat dieser Modul Zugriff auf dieselbe Funktion aus anderen Modulen
		- Beispiel
			```c++
			//fileA.cpp
			void func01()  //Deklaration
			{
				...        //Definition 
			}
			
			//fileB.cpp
			void func01(); //Deklaration
			
			//fileC.cpp
			void func01(); //Deklaration
			```
	- mit Attribut `static` $\Rightarrow$ lokale Größe: nur im <u>zugehörenden</u> Modul gültig 
- Ablauf ![](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Prog_cpp_Programm_Erzeugungsablaug.png) 

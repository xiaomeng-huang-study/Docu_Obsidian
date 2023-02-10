## Reihenfolge_Konstruktion-Destruktion 
![|375](https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/PROGCP_Reihenfolge_Konstruktion-Destruktion.jpg) 

## Initialisierungslist
- Reihenfolge: 1.Base 2.Member 3.Parameter
	```c++
	classB::classB(int p):
		Base(...),Member_Name(...),m(p)
	{
	
	}
	```
- 用父类初始化列表:用类名称; 用成员初始化列表:用object名
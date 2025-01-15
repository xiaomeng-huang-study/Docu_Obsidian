- Konstruktor
	- Schreibweise
		- keine Implementierungsinhalt
			- in .h: `classA(){};` 
		- mit Implementierungsinhalt
			- in .h: `classA();` 
			- in .cpp: `classA::classA(){...}` 
	- ==in Konstruktor== : <font color = "red">Initialisierung von privaten Attributen</font> 
		- keine Zeiger:
			```c++
			data = _data;
			```
		- mit Zeiger:
			```c++
			//Initializierung von Attributen
			data = _data;

			//Zeiger zeigt auf anderen Speicherbereich auf Heap
			Zeiger = new ...;

			#if 0 //Falls Zuweisung erforderlich
			for(int i = 0; i < dim; i++)
			{
				Zeiger[i] = ...;
			}
			#endif 
			```
	- ==in Aufrufer== : Konstruktion
		- keine Parameter: 
			- Standardkonstruktor `Flugzeug f1;` 
		- mit Parameter: 
			- `Flugzeug f2("British Airways");` 
	- Eigenschaften 
		- kann überladen werden 
	- 构造方式
		- **隐式调用无参构造函数** 
			- `Data ob1;` 
		- 显式调用无参构造函数
			- `Data ob2 = Data();` 
		- **隐式调用有参构造函数**
			- `Data ob3(10);` 
		- 显式调用有参构造函数
			- `Data ob4 = Data(10);` 
		- 匿名对象
			- `Data();` 
			- `Data(10);` 
- Destruktor 
	- Klasse enthält keine Zeiger $\Rightarrow$ nicht erforderlich 
	- Klasse enthält <font color = "red">Zeiger</font>  $\Rightarrow$  <font color = "red">Destruktor erforderlich</font> 
		- ==in Destruktor== 
			- `delete XXX;` 
			- `delete []XXX;` 
		- ==in Aufrufer== 
			- ohne `new` 
				- Destruktor wird automatisch aufgerufen 
					- Wann: `}` oder Prozess endet 
			- mit `new` 
				- Desktruktor wird bei `delete` aufgerufen 
	- Eigenschaften 
		- darf <u>nicht</u> überladen werden 
		- Reihenfolge: FILO
			- nach dem Prinzip vom Stack: zuerst konstruiert $\Rightarrow$ zuletzt destrukturiert
<br><div STYLE="page-break-after: always;"></div> 
- Beispiele
	- mit int\[\] 
		- Vector.h
			```c++
			#include <string>    //string
			#include <sstream>   //ostringStream
			#include <iostream>
			using namespace std;
			
			class Vector
			{
			public:
			    Vector(int _dim);
			    ~Vector();
			
			    void write(double* _vec);
			    string toString();
			private:
			    int dim;
			    double *vec;
			};
			```
		- Vector.cpp
			```c++
			Vector::Vector(int _dim):
			    dim(_dim)
			{
			    vec = new double [dim];
			}
			
			Vector::~Vector()
			{
			    delete []vec;
			}
			
			void Vector::write(double* _vec)
			{
			    for(int i = 0;i<dim;i++)
			    {
			        vec[i] = _vec[i];
			    }
			}
			
			string Vector::toString()
			{
			    ostringstream strStream;
			    for(int i =0;i<dim;i++)
			    {
			        strStream<<"["<<vec[i]<<"]"<<endl;
			    }
			    return strout.str();
			}
			```
	<br><div STYLE="page-break-after: always;"></div> 
	- mit char\[\] 
		- Data.h
			```c++
			#include <string.h>
			#include <iostream>
			using namespace std;
			
			class Data
			{
			public:
				Data(){}
				Data(char* str);
				~Data();
				  
				char* getData();
			protected:
			
			private:
				char *data;
			};
			```
		- Data.cpp
			```c++
			Data::Data(char* str)
			{
				data = new char[strlen(str)+1];
				strcpy(data,str);
				cout<<"Konstruktor mit Parameter"<<endl;
			}
			
			Data::~Data()
			{
				if(NULL!=data)
				{
					delete []data;
				}
				cout<<"Destruktor"<<endl;
			}
			
			char* Data::getData()
			{
				return data;
			}
			```
		<br><div STYLE="page-break-after: always;"></div> 
		- ![|500](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Prog%20C++_Konstruktion-Destruktion.png) 

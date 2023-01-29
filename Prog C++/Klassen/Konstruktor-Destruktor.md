- Konstruktor bzw. Destruktor
	- keine Implementierungsinhalt
		- in .h: `classA(){};` 
	- mit Implementierungsinhalt
		- in .h: `classA();` 
		- in .cpp: `classA::classA(){...}`
- Konstruktor
	- ==in Konstruktor== : <font color = "red">Initialisierung von privaten Attributen</font> 
		- keine Zeiger:
			```c++
			data = _data;
			```
		- mit Zeiger:
			```c++
			Zeiger = new int[dim];
			
			#if 0 //Falls Zuweisung erforderlich 
			for(int i = 0; i < dim; i++)
			{
			Zeiger[i] = _data.Zeiger[i]
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
<br><div STYLE="page-break-after: always;"></div> 
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
<br><div STYLE="page-break-after: always;"></div> 
- Beispiele
	- mit int\[\] 
		- Vector.h
			```c++
			#include <string>
			#include <sstream>
			
			#include <iostream>
			
			using namespace std;
			
			class Vector
			{
			public:
			    Vector(int _dim);
			    ~Vector();
			
			    void write(double* _vec);
			    string toString();
			
			protected:
			
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
			
			void Vector::write(double *_vec)
			{
			    for(int i = 0;i<dim;i++)
			    {
			        vec[i] = _vec[i];
			    }
			}
			
			string Vector::toString()
			{
			    ostringstream strout;
			    for(int i =0;i<dim;i++)
			    {
			        strout<<"["<<vec[i]<<"]"<<endl;
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
		- ![|500](https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/Prog%20C++_Konstruktion-Destruktion.png)
- 
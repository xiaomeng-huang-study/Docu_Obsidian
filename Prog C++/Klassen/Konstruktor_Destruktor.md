- Konstruktor
	- keine Parameter: 
		- Standardkonstruktor `Flugzeug f1;` 
	- mit Parameter: 
		- `Flugzeug f2("British Airways");` 
	- Eigenschaften 
		- kann überladen werden
- Destruktor
	- `~Flugzeug f3();` 
	- `}` oder Prozess endet $\Rightarrow$ Destruktor aufgerufen
	- mit Zeiger: Destruktor erforderlich 
	- Eigenschaften 
		- darf nicht überladen werden
		- Reihenfolge: FILO
- Beispiel
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
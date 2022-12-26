- Typen
	- ohne Zeiger $\Rightarrow$ flache Kopie
	- mit <u>dynamsichen Komponenten</u>(mit <u>Zeiger auf Heap)</u> $\Rightarrow$ <u>tiefe Kopie</u> erforderlich 
- Beispiel
	- Data.h
		```c++
		public: 
		/**
		 * Kopie Konstruktor
		 */
		Data(const Data& _data);
		
		/**
		 * const erforderlich
		 */
		char* getData () const;
		```
	- Data.cpp
		```c++
		Data::Data(const Data& _data)
		{
		    data = new char[strlen(_data.getData())+1];
		    strcpy(data,_data.getData());
		    cout<<"Kopie Konstruktor"<<endl;
		}
		
		char* Data::getData() const
		{
		    return data;
		}
		```
		
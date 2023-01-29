- Typen
	- Klasse enthält keine Zeiger
		- keine eigene Kopiekonstruktor erforderlich 
		- flache Kopie : `ob1 = ob2;` 
	- Klasse enthält <font color = "red">dynamsichen Komponenten</font>(mit <font color = "red">Zeiger auf Heap</font>) 
		- eigene Kopiekonstruktor definieren 
		- <font color = "red">tiefe Kopie</font> (ähnlich wie Konstruktor) 
			- <font color = "red">Initialisierung + Zuweisung</font> 
				```c++
				//Initializierung
				Zeiger = new int[dim];
				
				//Zuweisung 
				for(int i = 0; i < dim; i++)
				{
				Zeiger[i] = _data.Zeiger[i]
				}
				```
- Beispiele
	- mit int\[\] 
		- Vector.h
			```c++
			public:
			Vector(const Vector& _vector);
			```
		- Vector.cpp
			```c++
			Vector::Vector(const Vector& _vector)
			{
				//Initialisierung wie Konstruktor 
			    dim = _vector.dim;
			    vec = new double [dim];
				
				//Zuweisung erforderlich
			    for(int i=0;i<dim;i++)
			    {
			        vec[i] = _vector.vec[i];
			    }
			}
			```
	- mit char\[\]
		- Data.h
			```c++
			public: 
			Data(const Data& _data);
			```
		- Data.cpp
			```c++
			Data::Data(const Data& _data)
			{
				//Initialisierung wie Konstruktor
			    data = new char[strlen(_data.data)+1];
				
				//Zuweisung erforderlich
			    strcpy(data,_data.data);
			    cout<<"Kopie Konstruktor"<<endl;
			}
			```

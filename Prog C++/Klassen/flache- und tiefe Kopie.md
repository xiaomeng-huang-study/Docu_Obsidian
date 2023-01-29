- Klasse enthält keine Zeiger
	- flache Kopie 
	- keine eigene Kopiekonstruktor erforderlich 
	- ==in Aufrufer== 
		- `ob1 = ob2;` 
- Klasse enthält <font color = "red">dynamsichen Komponenten</font>(mit <font color = "red">Zeiger auf Heap</font>) 
	- <font color = "red">tiefe Kopie</font> 
	- eigene ==Kopiekonstruktor== definieren 
		```c++
		KlasseA(const KlasseA& _kA);

		KlasseA::KlasseA(const KlasseA& _kA)
		{
			//Initializierung von Attributen
			data = _kA.data;

			//Zeiger zeigt auf anderen Speicherbereich auf Heap
			Zeiger = new ...;

			//Zuweisung
			for(int i = 0; i < dim; i++)
			{
				Zeiger[i] = _kA.Zeiger[i];
			}
		}
		```
	- ==in Aufrufer== 
		```c++
			KlasseA ob1(...);
			KlasseA ob2(ob1);
			KlasseA ob3 = ob1;
		```
<br><div STYLE="page-break-after: always;"></div> 
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

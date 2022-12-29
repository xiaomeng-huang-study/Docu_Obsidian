## statische Polymorphie
- Überladen
	- Funktion überladen
	- Operator überladen
- redefining

## dynamische Polymorphie
- virtuelle Funktionen (virtual function)
	- überschreiben (override)

- `virtual` + `=0` $\Rightarrow$ abstrakte Klasse
	- Instanzierung verboten
	- Unterklasse muss alle virtuelle Methode überschreiben

- außer Konstruktor sollen mit `virtual` beschrieben werden.

- Aufbau
	- Oberklasse
		```c++
		public:
			Interface(){}               //keine virtual; keine = 0
			virtual ~Interface(){}      //virtual
			
			//nur Unterklasse kann func01 implementieren
			virtual void func01() = 0;  //virtual; = 0
			//Unterklasse wird diese func01 anders implementieren
			virtual void func02();      //virtual
			//Oberklasse und Unterklasse, beide haben diese Eigenschaft
			void func03();              //keine virtual; keine =0 
		```
	- Unterklasse
		```c++
		public: 
			Unterklasse(){}
			~Unterklasse(){}
		
			void func01();
		```

- Bedienung
	- Variante1
		```c++
		Polygon *p = new Polygon;
		p->draw();
		delete p;
		Polygon *p = new Tirangle;
		p->draw();
		delete p;
		```
	- Variante2
		- in Funktion kapseln
			```c++
			void painter(Polygon* p)
			{
				p.draw();   // kein delete erforderlich 
			}
			```
		- in Class kapseln 
			```c++
			public:
				Bedienklasse(){}
				~Bedienklasse(){}

				bool fuegeHinzu(Polygon* p);
			```
		- Aufruf (in `main()` )
			```c++
			Polygon p;
			Triangle t;
			painter(&p);
			painter(&t);
			```
	- Variante3 
		- in Funktion kapseln <font color = "red">delete erforderlich!</font> 
			```c++
			void painter(Polygon* p)
			{
				p->draw();
				delete p;
			}
			```
		- in Class kapseln <font color = "red">delete in Destruktor erforderlich!</font>
			```c++
			class Bedienklasse
			{
			public:
				Bedienklasse(){}
				~Bedienklasse();

				bool fuegeHinzu(Polygon* p);
			}
			Bedienklasse:: ~Bedienklasse()
			{
				delete ...;
			}
			```
		- Aufruf (in `main()` )
			```c++
			painter(new Polygon);
			painter(new Triangle);
			```
	- Variante4  
		```c++
		void painter(Polygon& p)
		{
			p.draw();
		}
		
		//in main()
		Polygon p;
		Triangle t;
		painter(p);
		painter(t);
		```

- Falls Unterklasse erweiterte Eigenschaft besitzt : type cast
```c++
void painter(Polygon* p)
{
	if('t' == p->identify())
	{
		Triangle* temp_t = NULL;
		temp_t = (Triangle*) p;
		temp_t->XXX();
	}
	p->draw();
	delete p;
}
```
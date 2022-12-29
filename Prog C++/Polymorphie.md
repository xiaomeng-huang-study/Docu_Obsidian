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
	- Interface
		```c++
		public:
			virtual ~Interface(){}
		
			virtual void func01() = 0;
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
		```c++
		void painter(Polygon* p)
		{
			p->draw();
			delete p;
		}
		
		//in main()
		painter(new Polygon);
		painter(new Triangle);
		```
	- Variante3 <font color = "red">Destruktor erforderlich!</font> 
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


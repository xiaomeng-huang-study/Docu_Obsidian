- Eigenschaften 
	- ein Zeiger, auf den nur innerhalb der <u>nichtstatischen Memberfunktionen</u> eines <u>class</u> zugegriffen werden kann.
	- Er <font color = "red">zeigt auf das Objekt</font>, für das die Memberfunktion aufgerufen wird.
	- Statische Memberfunktionen verfügen nicht über einen this Zeiger.
- Anwendung
	- Membervariable und Parameter haben gleichen Name
		- z.B. `this->a = a;` 
	- Memberfunktion mit `const` : Membervariable sind für diese Funktion nur lesbar (außerhalb mit `mutable` )
		- Beispiel
			```c++
			void getData() const
			{
				//a = 100; //ERROR
			}
			```
	- angekettete Operationen
		```c++
		class ClassA
		{
		public:
			ClassA& myPrintf(char* str)
			{
				cout<<str<<" ";
				return *this;
			}
		};
		
		void test01()
		{
			ClassA().myPrintf("1").myPrintf("2").myPrintf("3");
		}
		```
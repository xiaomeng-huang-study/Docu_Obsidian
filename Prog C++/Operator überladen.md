- links von Operator
	- nicht von mir definiert $\Rightarrow$ 2 Parameter + global überladen 
	- von mir definiert $\Rightarrow$ 1 Parameter + in Klasse definieren 
- globale Operator überladen: 2 Parameter
	- `<<` 
		```c++
		#include <iostream>
		using namespace std;
		
		ostream& operator<< (ostream& strm, classA& cA)
		{
			strm<<cA.XXX<<...<<endl;
			return strm;
		}
		```
		- in classA: `friend ostream& operator<< (ostream& strm, classA& cA);` 
	- `>>` 
		```c++
		#include <iostream>
		using namespace std;
		
		istream& operator>> (istream& strm, classB& cB)
		{
			strm>>cB.XXX;
			return strm;
		}
		```
		- in classB: `friend istream& operator>> (istream& strm, classB& cB);` 
- Operator überladen als Memberfunktion von class
	- `+` 
		```c++
		//in classA.h
		public:
		classA operator+ (classA& cA);
		//in classA.cpp
		classA classA::operator+ (classA& cA)
		{
			classA temp;
			temp.XXX = XXX + cA.XXX;
			return temp;
		}
		```
	- `==` 
		- in classB: 
			```c++
			//in classB.h
			public:
			bool operator== (classB& cB);
			//in classB.cpp
			bool classB::operator== (classB& cB)
			{
				if(XXX == cB.XXX())
				{
					return true;
				}else
				{
					return false;
				}
			}
			```
		- in main.cpp
			```c++
			cB B1();
			cB B2();
			if(B1==B2)    //B1.(oprator==) B2
			{
				cout<<"equal"<<endl;
			}
			```
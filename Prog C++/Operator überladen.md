- links von Operator
	- von mir definiert: 1 Parameter 
	- nicht von mir definiert : 2 Parameter
- globale Operator überladen
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
	- `>>` 
		```c++
		#include <iostream>
		using namespace std;
		
		istream& operator<< (istream& strm, classB& cB)
		{
			strm>>cB.XXX;
			return strm;
		}
		```

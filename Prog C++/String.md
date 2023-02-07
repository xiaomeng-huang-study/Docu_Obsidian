- String-Stream
	```c++
	#include <sstream>  //ostringstream
	#include <string>   //string
	using namespace std;
	
	ostringstream strStream;
	strStream<<...<<"\n";
	
	string outStr = strStream.str();
		//cout<<outStr;
		//return<<outStr;
	```
- `to_string()` 
	```c++
	string to_string(int val);     //%d
	string to_string(double val);  //%f
	string to_string(float val);   //%f
	```
	- Beispiel 
		```c++
			#include <iostream>
			#include <string>   //string to_string()
			using namespace std;
		
			string pi = "pi is " + to_string(3.1415926);
			string num = to_string(1+2+4+7+14) + " is a perfect number";
			cout<<pi<<endl;
			cout<<num<<endl;
		```
- String to array 
	```c++
	#include <string>
	#include <cstring>
	using namespace std;
	
	string str = "ABCD";
	char arr[str.length()+1];
	strcpy(arr,str.c_str());
	```
- char[] to String
	```c++
	#include <iostream>
	#include <string>
	using namespace std;
	
	char arr[] = {'A','B','C','D'};
	string str(arr);
	cout<<str<<endl;
	```
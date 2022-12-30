- auf Stack
	- mit Parameter: `A arr[] = {A(10),A(20),A(30),A(40),A(50)};` 
	- ohne Parameter: `A arr2[] = {A(),A(),A(),A(),A()};` 
- auf Heap
	```c++
	A *arr;
	arr = new A[5];   //Konstruktor ohne Parameter wird aufgerufen.
	delete []arr;
	```
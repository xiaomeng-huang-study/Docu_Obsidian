## in C
- ein Element 
	```c++
	//malloc
	int* Zeiger = NULL;
	Zeiger = (int*)malloc(1*sizeof(int));
	
	//Zuweisung
	*Zeiger = 1;
		// cout<<(*Zeiger)<<endl;
	
	//free
	free(Zeiger);
	```
- Feld
	- eindimensional 
		```c++
	    //malloc
	    int* Zeiger = NULL;
	    Zeiger = (int*)malloc(3*sizeof(int));
	
	    //Zuweisung
	    Zeiger[0] = 1;
	    Zeiger[1] = 2;
	    Zeiger[2] = 3;
	        //for(int i = 0; i<3; i++)
	        //{
	        //    cout<<Zeiger[i]<<endl;
	        //}
	
	    //free
	    free(Zeiger);
		```
	- mehrdimensional
		```c++
		
		```
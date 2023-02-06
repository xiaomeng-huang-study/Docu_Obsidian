- Lib
	- stdlib.h  
- ein Element 
	```c++
    //malloc
    int* Zeiger = NULL;
    if(env == c)
    {
        Zeiger = (int*)malloc(1*sizeof(int));
    }
    if(env == cpp)
    {
        Zeiger = new int;
    }

    //Zuweisung
    *Zeiger = 1;
        //cout<<(*Zeiger)<<endl;

    //free
    free(Zeiger);
	```
- Feld
	- eindimensional 
		```c++
	    int* Zeiger = NULL;
	    if(env == c)
	    {
	        //malloc
	        Zeiger = (int*)malloc(3*sizeof(int));
	    }
	    if(env == cpp)
	    {
	        //new
	        Zeiger = new int[3];
	    }
	
	    //Zuweisung
	    Zeiger[0] = 1;
	    Zeiger[1] = 2;
	    Zeiger[2] = 3;
	        //for(int i = 0; i<3; i++)
	        //{
	        //    cout<<Zeiger[i]<<endl;
	        //}
	
	    //free
	    if(env == c)
	    {
	        free(Zeiger);
	    }
	    if(env == cpp)
	    {
	        delete []Zeiger;
	    }
		```
	- mehrdimensional
		```c++
		//malloc
	    int** Zeiger = NULL;
	    Zeiger = (int**)malloc(3*sizeof(int*));
	    Zeiger[0] = (int*)malloc(1*sizeof(int));
	    Zeiger[1] = (int*)malloc(2*sizeof(int));
	    Zeiger[2] = (int*)malloc(3*sizeof(int));
	
	    //Zuweisung
	    Zeiger[0][0] = 11;
	    Zeiger[1][0] = 21;
	    Zeiger[1][1] = 22;
	    Zeiger[2][0] = 31;
	    Zeiger[2][1] = 32;
	    Zeiger[2][2] = 33;
	        //cout<<Zeiger[0][0]<<endl;
	        //cout<<Zeiger[2][1]<<endl;
	
	    //free
	    for(int i = 0; i<3; i++)
	    {
	        free(Zeiger[i]);
	    }
	    free(Zeiger);
		```

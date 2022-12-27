- struct
	```c++
	struct Point
	{
	    double x;
	    double y;
	    struct Point *next;
	};
	```
- append
	```c++
	void append(Point** headofList,double x,double y)
	{
	    //letztes Element zu finden
	
	    /**
	     * @brief newPoint
	     */
	    Point *newPoint = NULL;
	    newPoint = new Point;
	    newPoint->x = x;
	    newPoint->y = y;
	    newPoint->next = NULL;
	
	    if(NULL==(*headofList))
	    {
	        //List leer
	        *headofList = newPoint;
	    }else{
	        //List nicht leer
	        Point* currentElement = NULL;
	        currentElement = *headofList;
	
	        while(NULL!=currentElement->next)
	        {
	            currentElement = currentElement->next;
	        }
	
	        //if(NULL==currentElement->next)
	        currentElement->next = newPoint;
	    }
	}
	```
- removeLastElement
	```c++
	void removeLastElement(Point** headofList)
	{
	    //die letzte 2 Elemente zu finden
	
	    if(NULL==(*headofList))
	    {
	        //List leer
	        cout<<"Liste leer"<<endl;
	    }else
	    {
	        //List nicht leer
	        Point* currentElement = NULL;
	        currentElement = *headofList;
	        Point* previousElement = NULL;
	        previousElement = *headofList;
	
	        while(NULL!=currentElement->next)
	        {
	            previousElement = currentElement;
	            currentElement = currentElement->next;
	        }
	
	        //if(NULL==currentElement->next)
	        if(currentElement==previousElement)
	        {
	            //Suche bei 1.Element geblieben
	            delete currentElement;
	            (*headofList) = NULL;
	        }
	        else if(currentElement!=previousElement)
	        {
	            //mehr als 1 Element
	            delete currentElement;
	            previousElement ->next = NULL;
	        }
	    }
	}
	```
- insert (geordnet)
	```c++
	void insert(Point** headofList,double x,double y)
	{
	    //jedes Element durchlaufen, und eine geeignete Stelle zu finden
	
	    /**
	     * @brief newPoint
	     */
	    Point* newPoint = NULL;
	    newPoint = new Point;
	    newPoint ->x = x;
	    newPoint ->y = y;
	    newPoint ->next = NULL;
	
	    double &nx = newPoint ->x ;    //nx: new_x
	    double &ny = newPoint ->y ;    //ny: new_y
	
	    if (NULL==(*headofList))
	    {
	        //List leer
	        *headofList = newPoint;
	    }else
	    {
	        //List nicht leer
	        Point* currentElement = NULL;
	        currentElement = *headofList;
	        Point* previousElement = NULL;
	        previousElement = *headofList;
	
	        while(NULL!=currentElement &&
	                  (currentElement->x<nx ||
	                  currentElement->x==nx && currentElement->y<ny)
	              )
	        {
	            previousElement = currentElement;
	            currentElement = currentElement->next;
	        }
	
	        if(NULL==currentElement)
	        {
	            previousElement->next = newPoint;
	        }else
	        {
	            if(currentElement==previousElement)
	            {
	                //Suche bei 1.Element geblieben
	                newPoint->next = (*headofList);
	                *headofList = newPoint;
	            }else if(currentElement!=previousElement)
	            {
	                newPoint->next = currentElement;
	                previousElement->next = newPoint;
	            }
	        }
	    }
	}
	```
- printList
	```c++
	void printList(Point* headofList){
	    //jedes Element durchlaufen
	
	    if(NULL == headofList)
	    {
	        //List leer
	        cout<<"Liste leer"<<endl;
	    }else{
	        //List nicht leer
	        Point* currentElement = NULL;
	        currentElement = headofList;
	
	        while(NULL!=currentElement)
	        {
	            cout<<"x: "<<(currentElement->x);
	            cout<<" y: "<<(currentElement->y)<<endl;
	            currentElement = currentElement->next;
	        }
	        cout<<"EOL"<<endl;
	    }
	}
	```
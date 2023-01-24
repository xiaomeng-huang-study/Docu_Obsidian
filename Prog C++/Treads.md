Header-Datei:
```c++
#include <thread>
using namespace std;
```

```c++
#include <thread>
using namespace std;

void func01()
{
	this_thread::sleep_for(chrono::seconds(2));
}

void func02(int threadNr)
{
	
}

int main()
{
	thread Thread1(func01);
	...
	Thread1.join();

	const int numOfThreads = 3;
	threads t[numberOfThreads];
	for(int i = 0; i<numOfThreads; i++)
	{
		//Making Thread i
		t[i] = thread(func02,i);
	}

	for(int i = 0; i<numOfThreads; i++)
	{
		t[i].join();	
	}
}

```

- Mutex
```c++
#include <mutex>
mutex m;

m.lock();
...
m.unlock();
```

- Call by Reference
	```c++
	...
	t[i] = thread(func03,std::ref(...));
	```


- Beispiel: Primzahlsuche auf mehreren Threads
	```c++
	#include <iostream>
	#include <cmath>
	#include <chrono>
	#include <mutex>
	#include <thread>
	
	using namespace std;
	
	//Konstante
	#define numThreads 8
	
	//globale Variablen
	mutex m;
	std::chrono::time_point<std::chrono::system_clock> tstart, tend;
	
	void primzahl(int start, int ende, int numThread)
	{
	    //der Bereich, den dies Thread berechnet
	    m.lock();
	    cout<<"Thread "<<numThread<<"berechnet : "<<start<<" bis "<<ende<<endl;
	    m.unlock();
	
	    for(int i = start; i<=ende; i++)
	    {
	        bool istPrimzahl = true;
	        int ende_j = (int)sqrt(i);
	
	        for(int j = 2; j<= ende_j; j++)
	        {
	            if(0 == i%j)
	            {
	                istPrimzahl = false;
	                break;
	            }
	        }
	        if(true == istPrimzahl)
	        {
	            //cout<<i<<", ";
	        }
	    }
	
	    m.lock();
	        //berechnet die Zeit, die dies Thread braucht
	        tend = std::chrono::system_clock::now();
	        std::chrono::duration<double> elapsed_seconds = tend-tstart;
	        cout << "Thread "<<numThread<<" : " <<elapsed_seconds.count()<<"benoetigt."<<endl;
	    m.unlock();
	}
	
	int main()
	{
	    //Bereich
	    int start = 2;
	    int ende = 10000000;
	
	    //Bereich teilen
	    int teilBereich = ende/numThreads;
	
	    //mehere Threads erzeugen
	    thread arrThreads[numThreads];
	
	    //Die Zeitmessung beginnt
	    tstart = std::chrono::system_clock::now();
	
	    //Bereich auf Threads teilen
	    for(int i = 0; i<numThreads; i++)
	    {
	        if(0 == i)
	        {
	            //1.Thread
	            arrThreads[i] = thread(primzahl,start,teilBereich,i+1);
	        }else if(i == (numThreads-1))
	        {
	            //das letzte Thread
	            arrThreads[i] = thread(primzahl,(i*teilBereich+1),ende,i+1);
	        }else
	        {
	            //die andere Threads
	            arrThreads[i] = thread(primzahl,(i*teilBereich+1),(i+1)*teilBereich,i+1);
	        }
	    }
	
	    for(int i = 0; i<numThreads; i++)
	    {
	        arrThreads[i].join();
	    }
	
	    m.lock();
	        //berechnet die Zeit, die das Hauptprogramm benoetigt
	        tend = std::chrono::system_clock::now();
	        std::chrono::duration<double> elapsed_seconds = tend-tstart;
	        cout << "benoetigte Zeit im Hauptprogramm: "<<elapsed_seconds.count()<<endl;
	    m.unlock();
	
	    return 0;
	}
	```
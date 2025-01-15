- Header-Datei:
	```c++
	#include <thread>
	using namespace std;
	```

- workload
	```c++
	//ohne Parameter
	void func01()
	{
		...
	}
	
	//mit Parameter: call by value
	void func02(int threadNr)
	{
		...
	}
	
	//mit Parameter: call by reference
	void func03(int& p)
	{
		...
	}
	```

- Thread(s) erzeugen
	- ein Thread
		```c++
		thread Thread1(func01);  //ohne Parameter
		thread Thread2(func02,2);  //call by value
		thread Thread3(func03,std::ref(...));  //call by reference
		```
	- mehrere Threads
		```c++
		thread arrThread[3];
		arrThread[0] = thread(func01);
		arrThread[1] = thread(func02,1);
		arrThread[2] = thread(func03,std::ref(...));
		```

- JOIN : Aufrufer wartet bis dies Thread fertig
	```c++
	//ein Thread
	Thread1.join();
	
	//mehrere Threads
	for(int i = 0; i < numThreads; i++)
	{
		arrThread[i].join();
	}
	```

- thread_sleep function
	```c++
	#include <chrono>
	this_thread::sleep_for(chrono::seconds(2));
	this_thread::sleep_for(chrono::milliseconds(2));
	```

- Mutex
	```c++
	#include <mutex>
	//globale Variable
	mutex m;
	
	m.lock();
	...
	m.unlock();
	```

- Atomics
	```c++
	#include <atomic>
	
	std::atomic<int> value;
	```

- Hintergrund-Threads : detach()
	```c++
	thread t(func01);  //func01 als child
	t.detach();
	```
	- nicht mehr über `join()` koordinierbar 
<br><div STYLE="page-break-after: always;"></div> 
- Beispiel: Primzahlsuche auf mehreren Threads
	- 1) 
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
	- 2) 
		```c++
		#include <iostream>
		#include <cmath>
		#include <chrono>
		#include <thread>
		
		using namespace std;
		
		int i;
		
		void primzahl(int start, int ende)
		{
		    cout<<"Berechne Prizahlen im Bereich "<<start<<" bis "<<ende<<endl;
		
		    for(i = start; i<=ende; i++)
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
		}
		
		int main() {
		    //Bereich
		    int start = 2;
		    int ende = 10000000;
		
		    //Thread erzeugen
		    thread Thread1(primzahl,start,ende);
		
		    //Zeitmessung beginnt
		    int sec = 0;
		
		    while (i <= ende) {
		        //Suchevorgang noch nicht fertig
		        this_thread::sleep_for(chrono::seconds(1));
		        sec++;
		        cout<<sec<<"s: "<<i<<" erreicht. Zahlen/s: "<< (i/sec)<<endl;
		    }
		
		    if(i > ende)
		    {
		        Thread1.join();
		    }
		    cout<<"fertig"<<endl;
		
		    return 0;
		}
		```
Header-Datei:
```c++
#includ <threads>
using namespace std;
```

```c++
#includ <threads>
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
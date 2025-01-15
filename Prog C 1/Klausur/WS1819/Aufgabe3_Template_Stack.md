```c++
template <class T>
class Stack
{
public:
    Stack();
    void push(T);
    T pop();
private:
    int leererStack;
    T elemente[MaxAnzahl];
    int oben;
};

template <class T>
Stack<T>::Stack()
{
    leererStack = -1;
    oben = leererStack;
}

template <class T>
void Stack<T>::push(T neuesElement)
{
    if(oben >= (MaxAnzahl-1))
    {
        cout<<"Stack voll"<<endl;
        return;
    }
    elemente[++oben] = neuesElement;
}

template<class T>
T Stack<T>::pop()
{
    if(leererStack >= oben)
    {
        cout<<"Stack leer"<<endl;
        return std::numeric_limits<T>::max();   //#include <limits>
    }
    return elemente[oben --];
}
```
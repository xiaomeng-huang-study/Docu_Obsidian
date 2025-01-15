```c++
class Triebwerk
{

public:
    Triebwerk(std::string which_triebwerk);

    void erzeugen();
    void starten();
    void stoppen();

protected:

private:
    string Which_Triebwerk;
};

Triebwerk::Triebwerk(std::string which_triebwerk):
    Which_Triebwerk(which_triebwerk)
{

}

void Triebwerk::erzeugen(){
    cout<<Which_Triebwerk<<"es Triebwerk erzeugt"<<endl;
}

void Triebwerk::starten(){
    cout<<Which_Triebwerk<<"es Triebwerk gestartet"<<endl;
}

void Triebwerk::stoppen(){
    cout<<Which_Triebwerk<<"es Triebwerk gestoppt"<<endl;
}

```

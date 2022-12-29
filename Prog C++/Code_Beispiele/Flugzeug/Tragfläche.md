```c++
class Tragflaeche
{
public:
    Tragflaeche(string which_tragflaeche);
    ~Tragflaeche(){}
    
    Triebwerk m_Triebwerk;

    void erzeugen();
protected:

private:
    string Which_Tragflaeche;
};

Tragflaeche::Tragflaeche(string which_tragflaeche):
    m_Triebwerk(which_tragflaeche),
    Which_Tragflaeche(which_tragflaeche)
{

}

void Tragflaeche::erzeugen(){
    cout<<Which_Tragflaeche<<"e Tragflaeche erzeugt"<<endl;
}

```
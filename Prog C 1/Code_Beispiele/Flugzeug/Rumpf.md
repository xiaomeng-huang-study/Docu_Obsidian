```c++
class Rumpf
{
public:
    Rumpf();

    void erzeugen();

    Tragflaeche Left_Tragflaeche;
    Tragflaeche Right_Tragflaeche;

    Fahrgestell m_Fahrgestell;

protected:

private:

};

Rumpf::Rumpf():
    Left_Tragflaeche("Link"),Right_Tragflaeche("Recht")
{

}

void Rumpf::erzeugen(){
    cout<<"Rumpf erzeugt"<<endl;
}
```
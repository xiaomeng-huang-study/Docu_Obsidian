```c++
class Flugzeug
{
public:
    Flugzeug(){}

    void erzeugen();
    void starten();
    void landen();

    Seitenleitwerk m_Seitenleitwerk;
    Hoehenleitwerk m_Hoehenleitwerk;
    Rumpf m_Rumpf;

protected:

private:

};
```

```c++
void Flugzeug::erzeugen(){
    //Fahrgestell
    m_Rumpf.m_Fahrgestell.erzeugen();

    //Tragflaeche
    m_Rumpf.Left_Tragflaeche.m_Triebwerk.erzeugen();
    m_Rumpf.Left_Tragflaeche.erzeugen();
    m_Rumpf.Right_Tragflaeche.m_Triebwerk.erzeugen();
    m_Rumpf.Right_Tragflaeche.erzeugen();

    //Rumpf
    m_Rumpf.erzeugen();

    //Seitenleitwerk
    m_Seitenleitwerk.erzeugen();

    //Hoehenleitwerk
    m_Hoehenleitwerk.erzeugen();

    //Flug
    cout<<"Flugzeug erzeugt"<<endl;
}

void Flugzeug::starten(){
    m_Rumpf.Left_Tragflaeche.m_Triebwerk.starten();
    m_Rumpf.Right_Tragflaeche.m_Triebwerk.starten();

    cout<<"Flugzeug gestartet"<<endl;

    m_Rumpf.m_Fahrgestell.einfahren();
}

void Flugzeug::landen(){
    m_Rumpf.m_Fahrgestell.ausfahren();

    cout<<"Flugzeug gelandet"<<endl;

    m_Rumpf.Left_Tragflaeche.m_Triebwerk.stoppen();
    m_Rumpf.Right_Tragflaeche.m_Triebwerk.stoppen();
}
```
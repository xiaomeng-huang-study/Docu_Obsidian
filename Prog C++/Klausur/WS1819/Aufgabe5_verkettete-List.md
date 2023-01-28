```c++
struct PreisListe {
    double preis;
    PreisListe *next;
    void init();
    void insert(double preis);
    double sum();
};

void PreisListe::init()
{
    next = NULL;
}

void PreisListe::insert(double preis)
{
    //neuer Preis
    PreisListe* newPreis = NULL;
    newPreis = new PreisListe;
    newPreis->preis = preis;
    newPreis->next = NULL;

    if(NULL == next)
    {
        //List leer
        next = newPreis;
    }else
    {
        //List nicht leer
        newPreis->next = this->next;
        this->next = newPreis;
    }
}

double PreisListe::sum()
{
    if(next == NULL)
    {
        //List leer
        return 0;
    }else {
        //List nicht leer
        double summe = 0;
        PreisListe* currentElement = NULL;
        currentElement = next;

        while(NULL != currentElement)
        {
            summe += currentElement->preis;
            currentElement = currentElement->next;
        }
        return summe;
    }
}
```
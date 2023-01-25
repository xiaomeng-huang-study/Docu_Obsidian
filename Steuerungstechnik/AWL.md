- FC1
	```c++
	double FC1                      //FUNCTION FC1 : REAL
	(double x, double y, double z)
	{
	    //Eingagnsvariable:
	                                //VAR_INPUT
	    double A = x;               //      A : REAL;
	    double B = y;               //      B : REAL;
	    double C = z;               //      C : REAL;
	                                //END_VAR
	
	    double temp = A;            //LD A
	    temp *= B;                  //MUL B
	    temp /= C;                  //DIV C
	    return temp;                //ST FC1
	}
	```
- FB1
	```c++
	class FB1                   //FUNCTION_BLOCK FB1
	{
	public:
	    //Eingangsvariable:
	                            //VAR_INPUT
	    double X;               //      X : REAL;
	    double Y;               //      Y : REAL;
	    double Z;               //      Z : REAL;
	    double M;               //      M : REAL;
	                            //END_VAR
	
	    //Ausgangsvariable:
	                            //VAR_OUTPUT
	    double ERGEBNIS;        //      ERGEBNIS : REAL;
	                            //END_VAR
	
	    void ini(double x,double y,double z,double m)   //LD  X
	                                                    //FC1 Y,Z
	    {
	        X = x;
	        Y = y;
	        Z = z;
	        M = m;
	        ERGEBNIS = FC1(X,Y,Z) + M;                  //ADD M
	                                                    //ST ERGEBNIS
	    }
	};
	```
<br><div STYLE="page-break-after: always;"></div> 
- Program
	```c++
	int main()                      //PROGRAM Program_Name
	{
	    //Variable:
	                                //VAR
	    double WERT1 = 40.0;        //  WERT1 : REAL := 40.0;
	    double WERT2 = 50.0;        //  WERT1 : REAL := 50.0;
	    double WERT3 = 20.0;        //  WERT1 : REAL := 20.0;
	    double WERT4 = 40.0;        //  WERT1 : REAL := 40.0;
	
	    double AUSGABE;             //  AUSGABE : REAL;
	    FB1 INSTANZ;                //  INSTANZ FB1;
	                                //END_VAR
	
	    INSTANZ.ini(WERT1,WERT2,WERT3,WERT4);       //CAL INSTANCZ(
	                                                //  X : = WERT1,
	                                                //  Y : = WERT2,
	                                                //  Z : = WERT3,
	                                                //  M : = WERT4)
	
	    double erg = INSTANZ.ERGEBNIS;              //LD INSTANZ.ERGEBNIS
	    AUSGABE = erg;                              //ST AUSGABE
	
	    cout<<AUSGABE<<endl;
	    return 0;
	}
	```

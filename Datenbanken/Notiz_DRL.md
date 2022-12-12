- CREATE
	```mysql
	create TABLE Tabelle_Name(
	Attribut1_Name Attribut1_Datentyp,
	Attribut2_Name Attribut2_Datentyp
	
	)
	```
	- Constraints einsetzen 
		- 1. Möglichkeit 
			```mysql
				create TABLE Tabelle_Name(
			Attribut1_Name Attribut1_Datentyp Constraint_Typ,
			Attribut2_Name Attribut2_Datentyp
			
			)
			```
		- 2. Möglichkeit (als Beispiel: PK)
			```mysql
			create TABLE Tabelle_Name(
			Attribut1_Name Attribut1_Datentyp,
			Attribut2_Name Attribut2_Datentyp
			Constraint pk_(Tabelle_Name) PRIMARY KEY (Attribut1_Name)
			)
			```
	- Constraint_TYP
		- NOT NULL
		- PRIMARY KEY
			- eindeutig 
			- keine NULL-Werte
			- jede Tabelle sollte genau einen PK haben 
		- AUTO_INCREMENT
		- FOREIGN KEY
		- UNIQUE
		- DEFAULT
	- 
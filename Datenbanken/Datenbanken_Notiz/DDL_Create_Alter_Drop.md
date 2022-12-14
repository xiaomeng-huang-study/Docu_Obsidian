- **CREATE** 
	- **TABLE** 
		```mysql
		create TABLE Tabelle_Name(
		Attribut1_Name Attribut1_Datentyp,
		Attribut2_Name Attribut2_Datentyp
		)
		```
		- Constraints einsetzen 
			- 1. Möglichkeit 
				- Beispie: Default
					```mysql
					create TABLE Tabelle_Name(
					Attribut1_Name Attribut1_Datentyp Default '...',
					Attribut2_Name Attribut2_Datentyp
					)
					```
			- 2. Möglichkeit
				- Beispiel: PK
					```mysql
					create TABLE Tabelle_Name(
					Attribut1_Name Attribut1_Datentyp,
					Attribut2_Name Attribut2_Datentyp,
					Constraint pk_(Tabelle_Name) PRIMARY KEY (Attribut1_Name)
					)
					```
				- Bespiel: FK
					```mysql
						create TABLE child_tabele_name(
						Attribut1_Name Attribut1_Datentyp,
						Attribut2_Name Attribut2_Datentyp,
						Constraint fk_(child_table_name) FOREIGN KEY (Attribut1_Name) REFERENCES parent_table_name(PK) on Situation_Typ Strategie_Typ
						)
					```
		- Constraint_TYP
			- **NOT NULL** 
			- **PRIMARY KEY** 
				- eindeutig 
				- keine NULL-Werte
				- jede Tabelle sollte genau einen PK haben 
			- **AUTO_INCREMENT** 
			- **FOREIGN KEY** 
				- enthält FK: child_table
				- enthält PK: parent_table
				- Situation_Typ
					- **Delete** 
					- **Update** 
				- Strategie_Typ
					- **Restrict** : Falls entsprechender FK vorhanden, Anfrage wird abgelehnt 
					- **Cascade** : Reaktion wie in parent_table
					- **Set NULL** : Falls entsprechender FK vorhanden, wird der auf NULL eingestellt
			- **UNIQUE** : eindeutig 
			- **DEFAULT**
	- **VIEW** 
		```mysql
		create VIEW View_Name as
		select ...
		```

- **ALTER** 
	- Beispiel
		```mysql
		alter TABLE Tabelle_Name
		modify COLUMN Attribut_Name VARCHAR(30) NOT NULL;
		```

- **DROP** 
	- **Table** 
		```mysql
		drop TABLE Tabelle_Name
		```
	- **Database** 
		```mysql
		drop DATABASE Datenbank_Name
		```
	- **View** 
		```mysql
		drop VIEW View_Name
		```
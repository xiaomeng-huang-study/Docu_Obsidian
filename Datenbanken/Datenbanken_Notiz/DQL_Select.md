## where
- +logische Zusammenhänge
- +Unterabfragen
	- Modell
		```plantuml
		@startuml EXISTS/IN
		Entity A{
		* **PK**
		* FK
		}
		Entity B{
		* **PK**
		* FK
		}
		Entity C{
		* **PK**
		* FK
		}
		A ||.r.|{ B
		B }|.r.|| C
		@enduml
		```
	- **IN**
		- Eigenschaften
			- Unterabfrage kann auch selbst durchgeführt werden
			- kann auch mehrfach geschaltet werden
		- Syntax
			- 2 Tabellen
				```mysql
				select A.Anzeige
				from A
				where A.FK in (select B.PK 
							   from B
							   where B.Bedingung ...);
				```
			- 3 Tabellen
				```mysql
				select A.Anzeige
				from A
				where A.FK in (select B.PK
								from B
								where B.FK in (select C.PK
												from  C
												where C.Bedingung ...)
								);
				```
	- **EXISTS
		- Eigenschaften
			- die Attribute in Unterfrage ist auch für Hauptfrage zugriffbar --> Alias erforderlich 
		- Syntax
			- 2 Tabellen
				```mysql
				select A.Anzeige
				from A 
				where exists(select * 
							from B 
							where A.FK = B.PK
								and B.Bedingung ...);
				```
			- 3 Tabellen
				```mysql
				select A.Anzeige
				from A
				where exist(select *
							from B
							where A.FK = B.PK
								and exists(select *
										from C
										where B.FK = C.PK
										and C.Bedingung ...)
							);
				```

### mit JOIN ersetzen
- 2 Tabellen
	```mysql
	select A.Anzeige
	from A
	inner join B 
		on A.FK = B.PK
	where B.Bedingung ...;
	```
- 3 Tabellen
	```mysql
	select A.Anzeige
	from A
		inner join B
			on A.FK = B.PK
		inner join C
			on B.FK = C.PK
	where A.Bedingung
		and C.Bedingung;
	```
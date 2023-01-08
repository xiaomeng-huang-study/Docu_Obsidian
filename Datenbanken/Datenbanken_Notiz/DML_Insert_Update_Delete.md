- **INSERT (into)** 
	```mysql
	INSERT into Tabelle_Name 
		(Attribut1_Name,Attribut2_Name,...)
	VALUES(Attribut1_Wert,Attribut2_Wert,...);
	```
	- Unterabfrage möglich 
		```mysql
		insert into Tabelle_Name 
			(
				Attribut1_Name, 
				Attribut2_Name,
				...
			)
		VALUES
			(
				Attribut1_Wert,
				(select Attribut2_Name from Tabelle_Name where ...),
				 ...
			 );
		```
- **UPDATE** 
	```mysql
	UPDATE Tabelle_Name
		set Attribut1_Name = wert1,
			Attribut2_Name = wert2
		where ...;
	```
- **DELETE (from)** 
	```mysql
	DELETE from Tabelle_Name
		where ... ;
	```


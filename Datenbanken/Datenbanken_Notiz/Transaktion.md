- Anforderung: ACID
	- Atomicity (Atomarität)
		- Anweisungen innerhalb einer Transaktion können nicht weiter aufgeteilt werden $\Rightarrow$ Entweder <font color = "red">vollständig</font> oder <font color = "red">keine</font> 
	- Consistency (Konsistenz) 
		- Datenbank ist immer in einem konsistenten Zustand
- Isolationsebene ![|350](https://raw.githubusercontent.com/xiaomeng-huang-study/images/main/pictures_Obsidian/Datenbanken_Transaktionen_Isolationsebene.png)
	- Set
		```mysql
		SET SESSION TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
		```
- explizites Sperren
	```mysql
	select bestand from artikel where artikel_nr = 21013 FOR UPDATE;
	-- artikel_nr = 21013 ist gesperrt
	```
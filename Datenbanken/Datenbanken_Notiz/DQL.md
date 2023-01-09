- 1) **SELECT** 

- 2) **FROM** 
	- JOIN
		- INNER/ LEFT/ RIGHT JOIN
			```mysql
			FROM A INNER/ LEFT/ RIGHT JOIN B
				on A.FK = B.PK
			...
			```
			- `INNER` 
			- `LEFT` : Tabelle A wird vollständig dargestellt 
			- `RIGHT` : Tabelle B wird vollständig dargestellt 
		- CROSS JOIN
			- Kreuzprodukt
			```mysql
			FROM A CROSS JOIN B -- keine on Bedingung erfordlich
			...
			```
		- SELF JOIN
			```mysql
			SELECT k1.kunden_nr, k1.name
			FROM kunde as k1 
				INNER JOIN kunde as k2
					on k1.geworben_von = k2.kunden_nr
			WHERE k2.nachname = 'Manz';
			-- Alle Kunden, die vom Kunden 'Manz' geworben wurden
			```
			- Modell: ![|525](https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/Datenbanken_rekursive_1:n-Beziehung.png)
<br><div STYLE="page-break-after: always;"></div>
- 3) **WHERE** 
	- IN/ EXISTS
		- Modell ![|225](https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/DatenBanken_EXISTS-IN_Modell.png) 
		- IN
			- Eigenschaften
				- Unterabfrage kann auch selbst durchgeführt werden
				- kann auch mehrfach geschaltet werden
			- Syntax
				- 2 Tabellen
					```mysql
					SELECT A.Anzeige
					FROM A
					WHERE A.FK in (select B.PK 
								   from B
								   where B.Bedingung ...);
					```
				- 3 Tabellen
					```mysql
					SELECT A.Anzeige
					FROM A
					WHERE A.FK in (select B.PK
									from B
									where B.FK in (select C.PK
													from  C
													where C.Bedingung ...)
									);
					```
		- EXISTS
			- Eigenschaften
				- die Attribute in Unterfrage ist auch für Hauptfrage zugriffbar $\Rightarrow$ <font color = "red">Alias</font> erforderlich 
			- Syntax
				- 2 Tabellen
					```mysql
					SELECT A.Anzeige
					FROM A 
					WHERE exists(select * 
								from B 
								where A.FK = B.PK
									and B.Bedingung ...);
					```
				- 3 Tabellen
					```mysql
					SELECT A.Anzeige
					FROM A
					WHERE exist(select *
								from B
								where A.FK = B.PK
									and exists(select *
											from C
											where B.FK = C.PK
											and C.Bedingung ...)
								);
					```
<br><div STYLE="page-break-after: always;"></div>
- 4) **GROUP BY** 
	```mysql
	SELECT A 
	FROM XXX
	GROUP BY A;
	```
---
- 5) **HAVING** 
	```mysql
	SELECT artikel_nr, SUM(bestellmenge)
	FROM bestellposition
	WHERE artikel_nr < 21020 
		-- WHERE: Einschränkung für Attribut
	GROUP BY artikel_nr
	HAVING SUM(bestellmenge) > 2; 
		-- HAVING: Einschränkung für Aggregatfunktion
	```
---
- 6) **ODER BY** 
	- asc/ desc
<br><div STYLE="page-break-after: always;"></div>
- Logische Zusammenhang
	- `=` ; `<` ; `>` ; `<>(!=)` ; `>=` ; `<=` 
	- `in (`XXX, XXX`)`
	-  `BETWEEN` a `AND` b 
		- (XXX >= a AND XXX <= b) 
	-  `IS NULL`/ `IS NOT NULL` 
	- `LIKE 'XXX'`
		- `%` : kein, ein, beliebig viele Zeichen
		- `_` : genau ein Zeichen 
- Aggregatfunktionen
	- `COUNT()` 
	- `SUM()` 
	- `AVG()` 
	- `MIN()` 
	- `MAX()` 
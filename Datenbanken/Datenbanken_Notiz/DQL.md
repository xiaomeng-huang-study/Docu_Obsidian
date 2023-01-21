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
			- Modell: <img src="https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/Datenbanken_rekursive_1:n-Beziehung.png" alt="|300"  />
			<br><div STYLE="page-break-after: always;"></div>
- 3) **WHERE** 
	- IN/ EXISTS
		- Modell <img src="https://raw.githubusercontent.com/ICH-BIN-HXM/images/main/pictures_Obsidian/DatenBanken_EXISTS-IN_Modell.png" style="zoom:50%;" /> 
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
								   where B.Bedingung ...)
						   AND A.Bedingung ...;
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
											AND B.Bedingung ...)
							AND A.Bedingung ...;
					```
		- EXISTS
			- Eigenschaften
				- die Attribute in Unterfrage ist auch für Hauptfrage zugriffbar $\Rightarrow$ <font color = "red">Alias</font> erforderlich 
			- Syntax
				- 2 Tabellen
					```mysql
					SELECT A.Anzeige
					FROM A 
					WHERE exists(SELECT * 
								FROM B 
								WHERE A.FK = B.PK
									AND B.Bedingung ...)
							A.Bedingung ...;
					```
				- 3 Tabellen
					```mysql
					SELECT A.Anzeige
					FROM A
					WHERE exists(SELECT *
								FROM B
								WHERE A.FK = B.PK
										AND exists(SELECT *
													FROM C
													WHERE B.FK = C.PK
															AND C.Bedingung ...)
										AND B.Bedingung ...)
							AND A.Bedingung ...;
					```
<br><div STYLE="page-break-after: always;"></div>
- 4) **GROUP BY** 
	```mysql
	SELECT A.Anzeige
	FROM A
	GROUP BY A.Anzeige;
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
- 6) **ORDER BY** 
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
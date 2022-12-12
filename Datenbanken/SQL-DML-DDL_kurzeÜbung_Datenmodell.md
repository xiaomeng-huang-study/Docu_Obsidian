2)erstellen Sie ein View "KundenProOrt", die pro Wohnort die Anzahl Kunde ausgibt
```mysql
create VIEW KundenProOrt as
select w.ort, count(k.nr) as Anzahl_Kunden
from wohnort as w
inner join kunde as k
on w.nr = k.ortnr
group by k.ort;
```

3)Nutzen Sie jetzt die View "KundenProOrt", um nur die Orte auszugeben, in denen mehr als 200 Kunden wohnen.
```mysql
select kpo.ort
from KundenProOrt as kpo
where kpo.Anzahl_Kunde > 200;
```

4)Sollten Sie immer nur an den Orten interessiert sein, in denen mehr als 200 Kunden wohnen, wie würden Sie das dann lösen?
```mysql

```




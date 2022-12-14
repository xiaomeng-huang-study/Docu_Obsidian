1.Listen Sie die teuersten Fahrräder pro Hersteller (herstellernr) auf
```mysql
select hersteller, max(wert)
from fahrrad
group by hersteller;
```
PS: "join" nicht nötig: keine Info sind aus "hersteller" zu lesen

2.Listen Sie alle Kunden und deren zugehörigen Wohnorte. Die Liste soll nach dem Nachnamen absteigend sortiert ausgegeben werden
```mysql
select k.vorname, k.name, w.ort
from kunde as k
inner join wohnort as w
on k.ortnr = w.nr
order by k.name desc;
```
PS: "join" nicht nötig: keine Info sind aus "hersteller" zu lesen

3.Für jeden Wohnort(ort) , geben Sie an, wie viele Kunden dort wohnen. Es sollen nur die Orte gelistet werden, in denen mindestens 20 Kunden wohnen
```mysql
select w.ort, count(k.nr) as Anzahl
from kunde as k
inner join wohnort as w
on k.ortnr = w.nr
group by w.ort
having Anzahl >= 20;
```

4.Für alle Kunde, deren Nachname mit "M" anfäng: Je Kundengeschlecht, geben Sie den durchschnittlichen Tagesmietpreis der Vermietung an. Im Ergebnis sollen aber nur die Zeilen ausgegeben werden, deren durchschnittlicher Tagesmietpreis zwischen 20 und 50 liegt
```mysql
select k.geschlecht, avg(f.tagesmietpreis)
from kunde as k
inner join vermietung as v
on k.nr = v.kundennr
inner join fahrrad as f
on v.fahrradnr = f.nr
where k.name like 'M%'
group by k.geschlecht
having avg(f.tagesmietpreis) between 20 and 50;
```

(1) Listen Sie alle Fahrräder vom Hersteller 'Ghost' auf. Lösen Sie die Aufgabe mit IN
```mysql
select * 
from fahrrad as f
where f.herstellernr in (select nr 
						from hersteller as h
						where h.herstellername = 'Ghost');
```

(2) Geben Sie die Kunden (name, vorname) aus, die in 'Ulm' wohnen. Lösen Sie die Aufgabe mit EXISTS
```mysql
select k.name, k.vorname
from kunde as k
where exists(select * 
			from wohnort as w 
			where k.ortnr = w.nr
				and w.ort = 'Ulm');
```

(3) Welche Fahrräder (rahmennummer) wurden vom Monteur mit dem Namen 'Meier' bearbeitet? Lösen Sie die Aufgabe mi IN
```mysql
select f.rahmennummer
from fahrrad as f
where f.nr in(select i.fahrradnr 
			 from inspektion as i
			 where i.monteurnr in(select m.nr 
								 from monteur as m
								 where m.name = 'Meier')
			 );
```

(4) Welche Hersteller(bestellername) stellen Mountainbikes (typbezeichnung = 'MTB') her? Lösen Sie die Aufgaben mit EXISTS
```mysql
select h.herstellername
from hersteller as h
where exists(select * 
			from fahrrad as f
			where h.nr = f.herstellernr
				and exists(select * 
							from fahrradtyp as ft
							where f.fahrradtypnr = ft.nr
								and ft.typbezeichnung = 'MTB')
			);
```
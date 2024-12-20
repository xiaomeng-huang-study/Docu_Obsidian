![](https://cdn.staticaly.com/gh/xiaomeng-huang-study/images_01@master/img/202211211257514.png)

6)von den Bewertungen mit 5, wie viele Urlaub wurden je Ziel gemacht?
```mysql
select Ziel, count(*)
from Urlaub
where Bewertung = 5
group by Ziel;
```

7)Wie viele unterschiedlichen Bewertungen wurden insgesamt abgegeben?
```mysql
select count(distinct Bewertung)
from Urlaub;
```

8)Wie viele unterschiedlichen Bewertungen wurden je Reisegruppe abgegeben?
```mysql
select Reisegruppe, count(distinct Bewertung)
from Urlaub
group by Reisegruppe;
```

9)Von den Lastminute Urlauben, was ist die Gesamt-Urlaubsdauer pro Ziel?
Bitte nur die Zeile ausgeben, deren Gesamt-Urlaubsdauer länger als 2 Wochen
```mysql
select Ziel, sum(Dauer)
from
where Lastminute = 1    -- von den Lastminute Urlauben: Lastminute = 1
group by Ziel
having sum(Dauer) > 14
```



```mysql
SELECT artikel_nr,SUM(bestellmenge)
FROM bestellposition
WHERE artikel_nr < 21020
GROUP BY artikel_nr
HAVING SUM(bestellmenge) > 2
```


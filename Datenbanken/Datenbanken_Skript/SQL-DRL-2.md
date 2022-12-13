S12
```mysql
-- 1)
select f.title, l.name
from film as f
inner join language as l
on f.language_id = l.language_id
order by l.name,f.title;

-- 2)
select f.title, l.name
from film as f, language as l
where f.language_id = l.language_id
order by l.name, f.name;
```

S13
```mysql
select f.release_year, c.name, count(*)
from film as f
inner join film_category as fc
on f.film_id = fc.film_id
inner join category as c
on fc.category_id = c.category_id
group by f.release_year, c.name;
```

S20
```mysql
-- 1)
select l.name, f.film_id
from language as l
left join film as f
on l.language_id = f.language_id
where f.film_id is NULL;

-- 2)
select 
from film as f
right join language as l
on f.language_id = l.language_id
where f.film_id is NULL;
```
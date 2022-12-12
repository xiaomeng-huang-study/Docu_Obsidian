S6
```mySQL
select title
from film
where language_id = (select language_id
					from language
					where name = 'Englisch');
```

S9
```mysql
select l.name
from language as l
where language_id not in (select f.language_id
						 from film as f
						 );
```

```mysql
select l.name 
from language as l 
where not exists(select * 
				from film as f
				where l.language_id = f.language_id); 
```

S13
(1) mit IN
```mysql
select f.title
from film as f
where f.film_id in(select fa.film_id
					 from film_actor as fa
					 where actor_id = '5');
```

(2) mit EXISTS
```mysql
select f.title
from film as f
where exists(select *
		   from film_actor as fa
		   where fa.film_id = f.film_id  
			   and fa.actor_id = '5');
```

(2) mit INNER JOIN
```mysql
select f.title
from film as f
	inner join film_actor as fa
	on  f.film_id = fa.film_id
where fa.actor_id = '5';
```

S14
(1) mit IN
```mysql
select f.title
from film as f
where f.film_id in(select fc.film_id
				  from film_category as fc
				  where fc.category_id in(select c.category_id
										  from category as c
										  where c.name = 'Drama')
				  )
	  and f.release_year < 2008;
	```

(2) mit JOIN
```mysql
select f.title
from film as f
	inner join film_category as fc
		on f.film_id = fc.film_id
	inner join category as c
		on fc.category_id = c.category_id
where f.release_year < 2008
	and c.name = 'Drama';
```

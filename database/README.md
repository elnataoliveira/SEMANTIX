### import files to docker database

``` sh
docker cp input/exercises-data/db-sql/ database:/
docker exec -it database bash
```

### accessing docker database
``` sh
cd /db-sql/
```
``` sql
mysql -psecret < employees.sql
```
``` sh
cd /db-sql/sakila
```
``` sql
mysql -psecret < sakila-mv-schema.sql
mysql -psecret < sakila-mv-data.sql

```
#### append and increment
```
docker exec -it database bash
mysql -psecret
use sakila;
show tables;
select * from rental limit 5;

create table cp_rental_append select rental_id, rental_date from rental;

create table cp_rental_id select select * from cp_rental_append;


```

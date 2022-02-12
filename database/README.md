### import files to docker database

``` sh
docker cp input/exercises-data/db-sql/ database:/
docker exec -it database bash
```

### sql
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

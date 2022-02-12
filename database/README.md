### import files to docker database

``` sh

```

### sql

``` sql
``` sh
cd /db-sql/
```
mysql -psecret < employees.sql
``` sh
cd /db-sql/sakila
```
mysql -psecret < sakila-mv-schema.sql
mysql -psecret < sakila-mv-data.sql

```

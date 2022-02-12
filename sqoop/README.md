### sqoop

``` sqoop

sqoop list-databases --connect jdbc:mysql://database --username user --password pass

sqoop list-tables --connect jdbc:mysql://database/exemple --username user --password pass


sqoop eval --connect jdbc:mysql://database/exemple --username user --password pass --query "select * from employees limit 15"

sqoop eval --connect jdbc:mysql://database/exemple --username user --password pass --query "create table setor(cod int(2), name varchar(30))"

sqoop eval --connect jdbc:mysql://database/exemple --username user --password pass --query "describe setor"

sqoop eval --connect jdbc:mysql://database/exemple --username user --password pass --query "insert into setor values(1, 'vendas')"


sqoop eval --connect jdbc:mysql://database/exemple --username user --password pass --query "select * from setor"

sqoop eval --connect jdbc:mysql://database/exemple --username user --password pass --query "select * from employees where first_name like 'A'"

```
### exercise

``` sqoop
sqoop list-databases --connect jdbc:mysql://database --username root --password secret
sqoop list-tables --connect jdbc:mysql://database/employees --username root --password secret
sqoop eval --connect jdbc:mysql://database/employees --username root --password secret --query "insert into departments values('d010', 'BI')"
sqoop eval --connect jdbc:mysql://database/employees --username root --password secret --query "select * from departments"
sqoop eval --connect jdbc:mysql://database/employees --username root --password secret --query "create table benefits(cod int(2) auto_increment primary key, name varchar(30))"
sqoop eval --connect jdbc:mysql://database/employees --username root --password secret --query "insert into benefits values(null,'food vale')"
sqoop eval --connect jdbc:mysql://database/employees --username root --password secret --query "select * from benefits"

```

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

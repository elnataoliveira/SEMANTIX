### basic commands hadoop

``` sh
hdfs dfs -mkdir -p /user/aluno/elnataoliveira/data
hdfs dfs -mkdir -p /user/aluno/elnataoliveira/recover
hdfs dfs -mkdir -p /user/aluno/elnataoliveira/delete
hdfs dfs -ls -R /user/
hdfs dfs -put /input/exercises-data/entrada1.txt /user/aluno/elnataoliveira/data
hdfs dfs -ls -R /user/
hdfs dfs -ls -R /
hdfs dfs -put /input/exercises-data/escola/alunos.csv /user/aluno/elnataoliveira/data
hdfs dfs -ls -R /user/
hdfs dfs -tail /user/aluno/elnataoliveira/alunos.csv
hdfs dfs -tail /user/aluno/elnataoliveira/data/alunos.csv
hdfs dfs -tail 1 /user/aluno/elnataoliveira/data/alunos.csv
hdfs dfs -mv /user/aluno/elnataoliveira/entrada1.txt /user/aluno/elnataoliveira/data/recovery
hdfs dfs -mv /user/aluno/elnataoliveira/data/entrada1.txt /user/aluno/elnataoliveira/recover
hdfs dfs -ls -R /user/
hdfs dfs -find /user -name alunos.csv
hdfs dfs -tail /user/aluno/elnataoliveira/data/alunos.csv
hdfs dfs -cat /user/aluno/elnataoliveira/data/alunos.csv
hdfs dfs -cat /user/aluno/elnataoliveira/data/alunos.csv | head -n 2
hdfs dfs -checksum /user/aluno/elnataoliveira/data/alunos.csv | head -n 2
hdfs dfs -touchz /user/aluno/elnataoliveira/data/teste
hdfs dfs -c /user/aluno/elnataoliveira/data/teste
hdfs dfs -ls -R /user/
hdfs dfs -setrep 2 /user/aluno/elnataoliveira/data/teste
hdfs dfs -stat %r /user/aluno/elnataoliveira/data/alunos.csv
hdfs dfs -stat %o /user/aluno/elnataoliveira/data/alunos.csv
hdfs dfs -df -h /user/aluno/elnataoliveira/data/
hdfs dfs -du -h /user/aluno/elnataoliveira/data/
```
#### append and increment

``` sh
docker exec -it namenode bash
sqoop import --connect jdbc:mysql://database/sakila --username root --password secret --warehouse-dir /user/hive/warehouse/db_test3 -m 1 --table cp_rental_append
sqoop import --connect jdbc:mysql://database/sakila --username root --password secret --warehouse-dir /user/hive/warehouse/db_test3 -m 1 --table cp_rental_id
hdfs dfs -ls -h -R /user/hive/warehouse/db_test3
hdfs dfs -tail /user/hive/warehouse/db_test3/cp_rental_append/part-m-00000

docker exec -it namenode bash
sqoop import --connect jdbc:mysql://database/sakila --username root --password secret --warehouse-dir /user/hive/warehouse/db_test3 -m 1 --table cp_rental_append
sqoop import --connect jdbc:mysql://database/sakila --username root --password secret --warehouse-dir /user/hive/warehouse/db_test3 -m 1 --table cp_rental_id
hdfs dfs -ls -h -R /user/hive/warehouse/db_test3
hdfs dfs -tail /user/hive/warehouse/db_test3/cp_rental_append/part-m-00000
docker exec -it database bash
cd /db-sql/sakila/
cat insert_rental.sql
mysql -psecret < insert_rental.sql
docker exec -it namenode bash
sqoop import --table cp_rental_append --connect jdbc:mysql://database/sakila --username root --password secret --warehouse-dir /user/hive/warehouse/db_test3 -m 1 --append
sqoop eval --connect jdbc:mysql://database/sakila --username root --password secret --query "select * from cp_rental_append order by  rental_id desc limit 5"
sqoop import --table cp_rental_id --connect jdbc:mysql://database/sakila --username root --password secret --warehouse-dir /user/hive/warehouse/db_test3 -m 1 --incremental append --check-column rental_id --last-value 16049
sqoop import --table cp_rental_date --connect jdbc:mysql://database/sakila --username root --password secret --warehouse-dir /user/hive/warehouse/db_test3 -m 1 --incremental lastmodified --merge-key rental_id --check-column rental_date --last-value '2005-00823 22:50:12.0'
hdfs dfs -ls -R /user/hive/warehouse/db_test3
```

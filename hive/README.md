### copying files from local to hdfs

``` sh
docker exec -it namenode bash
ls /input/exercises-data/populacaoLA/
hdfs dfs -mkdir /user/aluno/elnataoliveira/data/populacao
hdfs dfs -put /input/exercises-data/populacaoLA/populacaoLA.csv /user/aluno/elnataoliveira/data/populacao
hdfs dfs -ls /user/aluno/elnataoliveira/data/populacao
hdfs dfs -cat /input/exercises-data/populacaoLA/populacaoLA.csv | head -n 3

```

### list databases on hive
``` sh
docker exec -it hive-server bash
beeline --help
beeline -u jdcb:hive2://localhost:10000
show databases;
create database elnataoliveira;
show databases;
use elnataoliveira
#create table elnataoliveira.pop
create table pop(
  zip_code int,
  total_population int,
  median_age float,
  total_males int,
  total_females int,
  total_households int,
  average_household_size float
)
  row format delimited
  fields terminated by ','
  lines terminated by '\n'
  stored as textfile
  tblproperties("skip.header.line.count"="1");
  desc pop;
  desc formatted pop;
  
```

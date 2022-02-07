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

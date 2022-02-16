### basic commands

### sending file from namenode

``` sh
docker exec -it namenode hdfs dfs -put /input/exercises-data/juros_selic /user/aluno/elnataoliveira/data
docker exec -it namenode hdfs dfs -ls /user/aluno/elnataoliveira/data
```

- access container docker spark

``` sh
docker exec -it spark bash
spark-shell
```

``` spark-shell

sc
spark
val jurosDF = spark.read.json("/user/aluno/elnataoliveira/data/juros_selic/juros_selic.json")
jurosDF.printSchema
jurosDF.show(5)
jurosDF.count
val jurosDF10 = jurosDF.where("valor > 10")
jurosDF10
jurosDF10.show(10)
jurosDF10.write.saveAsTable("elnataoliveira.tab_juros_selic")
val jurosHiveDF = spark.read.table("elnataoliveira.tab_juros_selic")
jurosHiveDF.printSchema
jurosHiveDF.show(5)
jurosHiveDF.write.save("/user/aluno/elnataoliveira/data/save_juros")
 val jurosHDFS = spark.read.load("/user/aluno/elnataoliveira/data/save_juros")
  val jurosHDFS = spark.read.load("/user/aluno/elnataoliveira/data/save_juros")
  jurosHDFS.printSchema
   jurosHDFS.show(5)
   
 
```


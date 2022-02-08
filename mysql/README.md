``` sql
insert into livraria_dw.dim_estado(id_dm_estado,nome_estado, sigla_estado)
select codigo_estado_ibge,nome_estado,sigla_estado from livraria.estado;
```

``` sql
insert into livraria_dw.dim_estado(id_dm_estado,nome_estado, sigla_estado)
select estado.codigo_estado_ibge, estado.nome_estado, estado.sigla_estado from livraria.estado;

insert into livraria_dw.dim_cidade(nome_cidade, id_dm_estado, cod_cidade_ibge)
select cidade.nome_cidade, cidade.id_dm_estado, cidade.cod_cidade_ibge from livraria.cidade;
```

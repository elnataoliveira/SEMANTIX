``` sql
insert into livraria_dw.dim_estado(id_dm_estado,nome_estado, sigla_estado)
select estado.codigo_estado_ibge, estado.nome_estado, estado.sigla_estado from livraria.estado;

insert into livraria_dw.dim_cidade(nome_cidade, id_dm_estado, cod_cidade_ibge)
select cidade.nome_cidade, cidade.id_dm_estado, cidade.cod_cidade_ibge from livraria.cidade;

DELIMITER $$

create procedure livraria_dw.CargaDimTempo()

BEGIN
	DECLARE ano, min, max INT;
	
	select MIN(ano_edicao) from livraria.livro into min;

	select MAX(ano_edicao) from livraria.livro into max;

	SET ano = min;
	WHILE ano <= max DO
		insert into livraria_dw.dim_tempo(ano) values(ano);
		set ano = ano + 1;
	END WHILE;
END
$$
DELIMITER;

```
### consultas
``` sql
use pesquisadb;
select count(a.cod_pessoa) as total_f_gato from pesquisa as A inner join pessoa as B on a.cod_pessoa = b.cod_pessoa where b.genero = 'Feminino' and a.cod_animal_estimacao = 104;
create temporary table homem_cha_frio_temp select l.genero, r.cod_bebida, l.data_nascimento from pessoa as L inner join pesquisa as R on l.cod_pessoa = r.cod_pessoa where l.genero = 'Masculino' and r.cod_bebida = 105 and r.cod_clima = 103;
SELECT avg(TIMESTAMPDIFF (YEAR, data_nascimento, CURDATE())) as idade FROM homem_cha_frio_temp;
create temporary table max_hobbie_mans select l.genero, r.cod_hobbie from pessoa as L inner join pesquisa as R on l.cod_pessoa = r.cod_pessoa where l.genero = 'Masculino';
create temporary table max_nome_hobbie_mans select l.genero, r.hobie from max_hobbie_mans as L inner join hobbie as R where l.cod_hobbie = r.cod_hobbie;
select count(hobie) as qntd, hobie from max_nome_hobbie_mans group by hobie order by qntd desc;
create temporary table tv_media_idade select l.cod_pessoa, r.cod_hobbie, l.data_nascimento from pessoa as L inner join pesquisa as R on l.cod_pessoa = r.cod_pessoa where r.cod_hobbie = 106;
SELECT avg(TIMESTAMPDIFF (YEAR, data_nascimento, CURDATE())) as idade FROM tv_media_idade;

select  count(r.cod_hobbie) as qntd, r.cod_hobbie, r.cod_animal_estimacao, l.genero from pessoa as L inner join pesquisa as R on l.cod_pessoa = r.cod_pessoa where l.genero = 'Feminino' and r.cod_animal_estimacao = 101 group by r.cod_hobbie order by qntd desc;
create temporary table idade_avg_ler select l.cod_pessoa, l.data_nascimento, r.cod_hobbie from pessoa as L inner join pesquisa as R on l.cod_pessoa = r.cod_pessoa where r.cod_hobbie = 101;
SELECT avg(TIMESTAMPDIFF (YEAR, data_nascimento, CURDATE())) as idade FROM idade_avg_ler;

select l.genero, r.cod_bebida, count(r.cod_bebida) as qntd from pessoa as L inner join pesquisa as R on l.cod_pessoa = r.cod_pessoa where l.genero = 'Masculino' group by r.cod_bebida order by qntd desc;
select l.genero, r.cod_bebida, count(r.cod_bebida) as qntd from pessoa as L inner join pesquisa as R on l.cod_pessoa = r.cod_pessoa where l.genero = 'Feminino' group by r.cod_bebida order by qntd desc;

select l.cod_pessoa from pessoa as L inner join pesquisa as R on l.cod_pessoa = r.cod_pessoa;

select * from idade_avg_ler;
select * from tv_media_idade;
drop table tv_media_idade;
select * from max_nome_hobbie_mans;
select * from homem_cha_frio_temp;
select * from animal_estimacao;
select * from bebida;
select * from clima;
select * from hobbie;

-- select floor(datediff (now(), data_nascimento)/365) as age from pessoa; --
SELECT TIMESTAMPDIFF (YEAR, data_nascimento, CURDATE()) as idade FROM pessoa;


```

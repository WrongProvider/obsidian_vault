## seleciona unicos
select distinct cpf, nome  from deputados;

select count (distinct  nome)  from deputados;

select * from deputados where id = 1; 

select * from deputados where id != 1; 

select * from deputados where id BETWEEN 1 AND 30; 

select * from deputados where nome like 'Kim%'; 

select * from deputados where 'siglaUF' in ('SP', 'RJ');

SELECT * FROM deputados  
ORDER BY nome ASC;

SELECT *  
FROM deputados  
WHERE 'siglaUF' = 'RJ' AND nome LIKE 'G%';
## CTEs

-- Exemplo de sintaxe para você testar no seu banco local:
```
WITH DadosInconsistentes AS (
    SELECT id, cpf FROM clientes_brutos WHERE status = 'erro'
),
BaseLimpa AS (
    SELECT id, cpf_formatado FROM mestre_clientes
)
SELECT d.id, b.cpf_formatado
FROM DadosInconsistentes d
JOIN BaseLimpa b ON d.id = b.id;
```

## Windows Functions 

-- Isso vai gerar um "ranking" (1, 2, 3...) para cada CPF repetido, -- colocando o mais recente sempre como 1

```
SELECT 
	id,
	cpf,
	data_atualizacao,
	ROW_NUMBER() OVER (PARTITION BY cpf ORDER BY data_atualizacao DESC) as rank_recente 
FROM clientes;
```


## EXPLAIN ANALYZE

-- Basta colocar EXPLAIN ANALYZE antes de qualquer SELECT pesado. 
```
EXPLAIN ANALYZE 
SELECT * FROM mestre_clientes WHERE data_cadastro > '2023-01-01'; 
```
-- O output não será a tabela de dados, mas sim um log detalhando os milissegundos -- gastos em cada etapa e se ele usou um "Index Scan" ou um "Seq Scan".

EXPLAIN ANALYZE 
SELECT * FROM deputados WHERE data > '2023-01-01';



Exercícios:
1-
WITH TotalTransacoes AS ( SELECT * from clientes_mdg GROUP BY cpf ) SELECT sum(d.valor) FROM TotalTransacoes d;

2-
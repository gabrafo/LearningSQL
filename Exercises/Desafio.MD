# LearningSQL

## Comandos
-  Selecione os nomes de cidade distintas que existem no estado de Minas Gerais em ordem alfabética (dados da tabela sales.customers).
```sql
SELECT DISTINCT city FROM sales.customers WHERE state = 'MG' ORDER BY city;
```

- Selecione o visit_id das 10 compras mais recentes efetuadas dados da tabela sales.funnel).
```sql
SELECT visit_id FROM sales.funnel 
WHERE paid_date IS NOT NULL
ORDER BY paid_date DESC LIMIT 10;
```

- Selecione todos os dados dos 10 clientes com maior score nascidos após 01/01/2000 (dados da tabela sales.customers).
```sql
SELECT * FROM sales.customers
WHERE birth_date > '2000-01-01'
ORDER BY score DESC
LIMIT 10;
```

## Operadores
- Calcule quantos salários mínimos ganha cada cliente da tabela sales.customers. Selecione as colunas de: email, income e a coluna calculada "salários mínimos"
OBS: Considere o salário mínimo igual à R$1200
```sql
SELECT email, income,
ROUND(income/1200) as "salários mínimos"
FROM sales.customers;
```


- Na query anterior acrescente uma coluna informando TRUE se o cliente ganha acima de 5 salários mínimos e FALSE se ganha 4 salários ou menos.
OBS: Chame a nova coluna de "acima de 4 salários"
```sql
SELECT email, income,
ROUND(income/1200) as "salários mínimos",
(ROUND(income/1200) > 4) as "acima de 4 salários"
FROM sales.customers;
```


- Na query anterior filtre apenas os clientes que ganham entre 4 e 5 salários mínimos. Utilize o comando BETWEEN.
```sql
SELECT email, income,
(income/1200) as "salários mínimos",
((income/1200) > 4) as "acima de 4 salários" 
FROM sales.customers
WHERE (income/1200) BETWEEN 4 AND 5;
```

- Selecine o email, cidade e estado dos clientes que moram no estado de Minas Gerais e Mato Grosso. 
```sql
SELECT email, city, state 
FROM sales.customers 
WHERE state NOT IN ('MG','MT');
```


- Selecine o email, cidade e estado dos clientes que não moram no estado de São Paulo.
```sql
SELECT email, city, state FROM sales.customers WHERE state <> 'SP';
```
OBS: <> significa "diferente".


-  Selecine os nomes das cidade que começam com a letra Z.
OBS: Dados da tabela temp_tables.regions
```sql
SELECT city FROM temp_tables.regions WHERE city ILIKE 'z%';
```

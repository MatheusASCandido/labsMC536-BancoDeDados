# Lab05 - Marcadores e Taxonomia em Cypher

Estrutura de pastas:

~~~
├── README.md  <- arquivo apresentando a tarefa
~~~

# Aluno
* `RA 241640`: `Matheus Augusto da Silva Cândido`

## Tarefa de Cypher sobre Marcadores e Taxonomia

## Tarefa 1

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, sem considerar as categorias subordinadas.


### Resolução
~~~cypher
MATCH(m)-[:Pertence]->(:Categoria{id: 'Serviços'}) RETURN m
~~~

## Tarefa 2

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, considerando as categorias subordinadas.

### Resolução
~~~cypher
MATCH(m)
WHERE (m)-[:Pertence]->()-[:Superior*1..]->({id: 'Serviços'}) OR (m)-[:Pertence]->({id: 'Serviços'})
RETURN  DISTINCT m
~~~
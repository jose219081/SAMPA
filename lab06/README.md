## OBS: O laboratório foi realizado na versão 5 devido a disponibilidade do neo4j pelo browser

Estrutura de pastas:

~~~
├── README.md  <- arquivo apresentando a tarefa
~~~

# Equipe `PLAY`

# Subgrupo `SAMPA`
* `José Felipe Theodoro` - `219081`
* `Gustvao Henrique Luiz Merlo` - `171401`

## Tarefa de Cypher sobre Patologias, Medicamentos e Efeitos Colaterais

## Exercício

Faça a projeção em relação a Patologia, ou seja, conecte patologias que são tratadas pela mesma droga.

### Resolução
~~~cypher
MATCH (p1:Pathology)<-[a]-(d:Drug)-[b]->(p2:Pathology)
MERGE (p1)<-[r:Relates]->(p2)
ON CREATE SET r.weight=1
ON MATCH SET r.weight=r.weight+1
~~~

# Trabalhando com Efeitos Colaterais

## Exercício

Construa um grafo ligando os medicamentos aos efeitos colaterais (com pesos associados) a partir dos registros das pessoas, ou seja, se uma pessoa usa um medicamento e ela teve um efeito colateral, o medicamento deve ser ligado ao efeito colateral.

### Resolução
~~~cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/santanche/lab2learn/master/data/faers-2017/sideeffect.csv' AS line
CREATE (:Collateral { code: line.codePathology, idperson:line.idPerson})

MATCH (d:Drug)-[t:Treats]->(p:Pathology)
MATCH (c:Collateral)
WHERE t.person = c.idperson
MERGE (d)-[sd:Sideeffects]->(c)
ON CREATE SET sd.weight=1
ON MATCH SET sd.weight=sd.weight+1
~~~

## Exercício

Que tipo de análise interessante pode ser feita com esse grafo?

Proponha um tipo de análise e escreva uma sentença em Cypher que realize a análise.

### Resolução
Podemos verificar quais são os efeitos colaterais mais comuns para todos medicamentos existentes

~~~cypher
MATCH (d1)-[sd:Sideeffects]->(c1)
MATCH (d2)-[sd:Sideeffects]->(c2)
WHERE c1.code = c2.code
RETURN c1.code, COUNT(*);
~~~

Estrutura de pastas:

~~~
├── README.md  <- arquivo apresentando a tarefa
│
└── images     <- arquivos de imagem usados na tarefa
~~~

# Equipe `PLAY`

# Subgrupo `SAMPA`
* `José Felipe Theodoro` - `219081`
* `Gustavo Henrique Luiz Merlo` - `171401`

## Modelo Lógico do Banco de Dados de Grafos
> ![Modelo Lógico de Grafos](images/modelo-logico-grafos.png)

## Perguntas de Pesquisa/Análise Combinadas e Respectivas Análises

### Pergunta/Análise 1
> * Como ocorre o fluxo de dados no grafo? (Centralidade)
>   
>   * O grafo mostra a alta centralidade do nó Recipes, indicando que o fluxo de dados passa necessariamente por ele para conectar a maioria das informações contidas nos demais nós. 

### Pergunta/Análise 2
> * Quais as consequências de perda de dados de Recipes? (Vulnerabilidade)
>   
>   * Como podemos verificar no grafo e na pergunta anterior podemos identificar a alta importância de Recipes o que torna possível afirmar que  existe um alto grau de vulnerabilidade nessa organização, pois a perca de dados contidos em Recipes podem tornar as informações de outros nós inutilizáveis. Um exemplo seria a perda das informações acerca "Cooked_Status: int", tal perda faria com que as informações presentes no nó Cooked_Status percam sua utilidade.

### Pergunta/Análise 3
> * É possível modularizar o grafo? (Modularidade)
>   
>   * Podemos identificar duas comunidades no grafo: a primeira uma ligação entre Recipes e seus nós adjacentes, e a segunda um ligação entre FCID_Code_Description e FCID_Cropgroup_Description. A informação contida na segunda comunidade é independente da primeira, o que indica que o grafo pode ser modularizado.

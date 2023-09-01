# Modelagem Relacional de Refeições em um Restaurante

Estrutura de pastas:

~~~
├── README.md  <- arquivo apresentando a tarefa
│
└── ER  <- arquivos de imagem ER, revisado
~~~

# Equipe
# Subgrupo SAMPA

* José Felipe Theodoro - RA:219081
* Gustavo Henrique Luiz Merlo - RA:171401

## Modelo conceitual ER Revisado
<img src="ER.jpg" width="400px" height="auto">

## Mapeamento para o Modelo Relacional

~~~
PESSOA(_Código_, Nome, Telefone)
ARMÁRIO(_Código_, Tamanho, Ocupante)
  Ocupante chave estrangeira -> PESSOA(Código)

~~~

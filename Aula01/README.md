# Conceitos

## Armazenamento Secundário (Disco)
Um disco é composto por múltiplos **pratos/discos** e pela **cabeça de leitora**; todo prato tem duas superfícies (em cima e embaixo). **Trilhas** são círculos concêntricos (com o mesmo centro); **setores** são a menor unidade endereçável de um disco, e são fatias longitudionais (pedaços de pizza). Setores são separados entre si por espaços sem dados armazenaos chamados de **gaps**. **Cilindros** são trilhas que estão na mesma circuferência/latitude ao longo de múltiplos pratos. A capacidade total de um disco pode ser calculado multiplicando o número de cilindros, o número de cabeçotes e o número de setores por trilha.

A superfície de um prato é dividida em malhas magneticamente polarizadas que representam 0 (zeros) e 1 (uns). O cabeçote de leitora pode ser usado para ler essas informações ou alterá-las usando um forte ímã magnético.

## Arquivo
Sequência de bytes armazenada em disco.

### Campo/Registro
**Struct**: composta por **campo/elemento/atributo**.

A struct é similar ao registro e o campo é similar aos elementos; uma struct possui vários elementos e um registro possui vários campos. A struct e elemento estão na memória principal, enquanto o **registro e o campo estão na memória secundária**.
# Conceitos

## Armazenamento Secundário (Disco)
Um disco é composto por múltiplos **pratos/discos** e pela **cabeça de leitora**; todo prato tem duas superfícies (em cima e embaixo). **Trilhas** são círculos concêntricos (com o mesmo centro); **setores** são a menor unidade endereçável de um disco, e são fatias longitudionais (pedaços de pizza). Setores são separados entre si por espaços sem dados armazenaos chamados de **gaps**. **Cilindros** são trilhas que estão na mesma circuferência/latitude ao longo de múltiplos pratos. A capacidade total de um disco pode ser calculado multiplicando o número de cilindros, o número de cabeçotes e o número de setores por trilha.

A superfície de um prato é dividida em malhas magneticamente polarizadas que representam 0 (zeros) e 1 (uns). O cabeçote de leitora pode ser usado para ler essas informações ou alterá-las usando um forte ímã magnético.

## Arquivo
Sequência de bytes armazenada em disco.

*Byte offset*: deslocamento a partir do 1º byte.

### Campo/Registro
**Struct**: composta por **campo/elemento/atributo**.

A struct é similar ao registro e o campo é similar aos elementos; uma struct possui vários elementos e um registro possui vários campos. A struct e elemento estão na memória principal, enquanto o **registro e o campo estão na memória secundária**.

OBS: priorizar sempre a busca, ou seja, tamanho fixo.

#### Campos
Em um arquivo, como saber onde começa e termina um campo?

```C
// Struct com tamanho fixo/exclusivo
struct pessoa1{
    char[100] nome;
    char[100] endereco;
    char[9] telefone;
    char[50] cidade;
    char[2] estado;
}

// Struct com tamanho variável
struct pessoa2{
    char* nome;
    char* endereco;
    char[9] telefone;
    char* cidade;
    char[2] estado;
}
```

Campo de **tamanho fixo**: conseguimos saber onde o campo começa e termina e a busca é facilitada, mas desperdiçamos espaço ou pode não haver espaço suficiente (truncamento). Usamos um caractere específico para separar lixo dos dados que queremos (como '\0', por exemplo). 

Campo de **tamanho variável**: 2 métodos, indicador de tamanho e delimitadores.

*Indicador de tamanho*: o tamanho do campo é armazenado (em bytes) logo antes do dado. Economiza espaço (nos dados) e não há truncamento, mas dificulta a busca (leitura byte a byte, sem fórmula matemática direta). Sem necessidade de caractere de separação.

*Delimitadores*: caracteres especiais são colocados entre os campos. Mesmas vantagens e desvantagens, mas dificulta a pesquisa e a escolha do do delimitador precisa ser correta.

OBS: caso um campo seja de tamanho fixo, ele **NÃO** deve ter delimitador e não deve estar no meio do registro! Deve estar no começo ou no fim.

#### Registros
Registros de **tamanho fixo**: podem ter campo de tamaho fixo **ou** variável!

Registros de **tamanho variável**: cada registro começa com um indicador de tamanho ou há delimitadores entre registros. Idem.

**Relative Record Number (RRN)**: usado para registro de tamanho fixo, fornece a posição relativa de cada registro dentro do arquivo (calcula o byte offset do registro). *byte offset* = RRN x tamanho do registro. *"O 1º registro tem RRN = 0, o 2º tem RRN = 1, ..."*.
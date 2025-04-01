# Abordagem Estática de Reuso do Espaço
## Manipulação de dados
- **Operações**
    - Inserção de registros
    - Remoção de registros -> remoção lógica
      - **Atribui um valor para um campo** (*)
      - Usa um campo extra (removido = 0 ou 1)
    - Atualização de registros

### Remoção de registros
- **Atribuição de valor a um campo**: substitui o primeiro caractere do primeiro campo por um caractere especial que serve para indicar que aquele registro está apagado
  - Abordagem **estática**
    - **NÃO** substitui um registro excluído, simplesmente adiciona no espaço vazio no final do arquivo
    - Compactação de arquivos: utiliza 2 arquivos
      - Lê todo o arquivo já existente
      - Escreve sequencialmente no segundo arquivo todos os registros não marcados como removidos

## Operações
**Busca** por RRN:
```
abrir arquivo para leitura

byte offset = RNN * tamRegistro

posicionar a posição corrente para o byte offset

se encontrou o registro E não foi marcado como excluído
    retorna o registro
senão
    retorna registro não encontrado

fechar arquivo
```
**Inserção**:
```
abrir arquivo para escrita

posicionar a posição corrente para o fim do arquivo

escrever o registro

fechar arquivo
```
**Remoção** por RRN:
```
abrir o arquivo para escrita

byte offset = RRN * tamRegistro

posicionar a posição corrente no byte offset

se encontrou o registro
    marcar como removido (sobrescreve a marcação, ok)

fechar o arquivo
```
**Compactação** de arquivos:
```
abrir arquivo 1 para leitura
criar e abrir arquivo 2 para escrita

enquanto a posição corrrente não for o fim do arquivo 1 E a quant. de registros removidos != 0:
    ler o registro
    se o registro não for marcado como excluído
        escrever esse registro no arquivo 2
    avançar posição corrente

fechar arquivo 1
fechar arquivo 2

deletar arquivo 1
renomear arquivo 2 para arquivo 1
```
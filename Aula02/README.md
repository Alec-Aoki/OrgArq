# Abordagem Estática de Reuso do Espaço
## Manipulação de dados
- **Operações**
    - inserção de registros (OK)
    - remoção de registros -> remoção lógica
      - **atribui um valor para um campo** (*)
      - usa um campo extra (removido = 0 ou 1)
    - atualização de registros
#### Remoção de registros
**Atribuição de valor a um campo**: substitui o primeiro caractere do campo por um caractere especial que serve para indicar que aquele campo está apagado
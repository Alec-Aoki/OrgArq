# Abordagem Dinâmica de Reuso de Espaço
- Caso haja um registro removido, ele será substituído por um registro novo;
- Estratégias;
  - First-Fit -> primeiro espaço que servir;
  - Best-Fit -> espaço mais justo possível (menor fragmentação interna);
  - Worst-Fit -> maior espaço possível (maior fragmentação interna);

## Registros de Tamanho Fixo
- **PILHA**
  - Encontra o registro a ser removido;
  - Coloca o caractere de remoção lógica;
  - Atualiza prox com o valor no topo da pilha;
  - Empilha o byteOffset.

## Registros de Tamanho Dinâmico
- **PILHA**
  - Encontra o registro a ser removido;
    - Contanto campos/pipes OU pelo delimitador de registros;
    - Marca como removido;
    - Guarda tamanho do registro;
    - Atualiza prox com o valor no topo da pilha;
    - Empilha byteOffset.
- Como melhorar? **LISTA ORDENADA** (pelo tamanho do registro)
  - Inserção rápida;
  - Remoção demorada;
  - Best-Fit: ordenação crescente;
  - Worst-Fit: ordenação decrescente;
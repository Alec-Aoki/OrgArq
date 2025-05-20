# Árvore B
- Método genérico de armazenamento e recuperação de dados;
  - Voltada para arquivos volumosos;
  - Rápido acesso aos dados;
  - Custo mínimo de *overhead*;
- Características:
  - Balanceada;
  - Bottom-up (construída das folhas para a raíz);
  - Nó = página de disco (tam. fixo = 4k bytes);
    - Sequência ordenada de chaves;
    - ```quant ponteiros``` = ```quant chaves``` + 1;
    - Ordem:
      - Knuth 1973;
      - Ordem = quantidade de ponteiros;
    - Observação: chave de busca e byteOffset andam de mãos dadas.

## Busca
- Recursiva, a partir do nó raíz (nó raíz guardado no cabeçalho);
- 2 estágios:
  - Entre páginas;
  - Dentro de páginas -> busca binária;
- Pegar RRN da raiz;
- Buscar dentro desse nó;
- Se não encontrar, chamar recursivamente com o RRN do nó correto.

## Inserção
- Sempre realizada nos nós **folhas**;
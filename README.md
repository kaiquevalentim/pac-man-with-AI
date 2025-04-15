# Busca em largura

## Solver sem poda com matriz 4x4

Iterações: 91435

## Solver com poda com matriz 4x4

### Impedindo nodos iguais ao pai

Iterações: 5660

**OBS:** A criação de novos nodos é feita a partir de tentativas de movimentos em todas as direações, se inciando pela direita (right). Quando alterado para iniciar as verificações com o movimento para baixo (down), o algoritmo levou mais iterações mas alcançou o mesmo resultado.

### Definindo g para caminhos com ou sem comida

- Se o próximo movimento for um caminho com comida, o valor de g é 0.
- Se o próximo movimento for um caminho sem comida, o valor de g é 1.
  
Iterações: 5367

### Impedindo nodos iguais à posição atual

- Junto a isso, foi removido o impedimento de gerar nodos iguais ao pai
  
Iterações: 804

## Conclusões

- Ao aumentar o campo para 5x5, o algoritmo de busca em largura levou X iterações, tornando-se inviável
- A busca em largura com poda se mostrou mais eficiente que a busca em largura sem poda, mesmo com o aumento do número de iterações
- Uma desvantagem da utilização de um algoritmo de busca em largura é a prioridade de nodos mais antigos frente a nodos mais recentes, porém, com melhores perspectivas de resolução do problema

# Busca em profundidade

## Solver sem poda com matriz 4x4

Iterações:

## Solver com poda com matriz 4x4

Iterações: 1880

OBS: As podas utilizadas são as mesmas desenvolvidas na busca em largura. 
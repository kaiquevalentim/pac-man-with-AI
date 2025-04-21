# Modelagem

## Definindo g para caminhos com ou sem comida

- Se o próximo movimento for um caminho com comida, o valor de g é 0.
- Se o próximo movimento for um caminho sem comida, o valor de g é 1.

# Busca em largura

## Solver sem poda com matriz 4x4

Iterações: 804

## Solver com poda com matriz 4x4

Iterações: 73

## Solver com poda para todos os campos

- Field 1: 73 iterações
- Field 2: 1175 iterações
- Field 3: 11465 iterações
- Field 4: 17126 iterações

## Conclusões

- Ao aumentar o campo para 5x5, o algoritmo de busca em largura sem poda gastou um tempo muito grande, tornando-se inviável
- A busca em largura com poda se mostrou mais eficiente que a busca em largura sem poda
- Uma desvantagem da utilização de um algoritmo de busca em largura é a prioridade de nodos mais antigos frente a nodos mais recentes, mesmo com esses tendo melhores perspectivas de resolução do problema

# Busca em profundidade

## Solver sem poda com matriz 4x4

Iterações: 1880

## Solver com poda com matriz 4x4

Iterações: 98

OBS: As poda utilizada é a mesma desenvolvida na busca em largura. 

## Solver com poda para todos os campos

- Field 1: 98 iterations
- Field 2: 1389 iterations
- Field 3: 11367 iterations
- Field 4: 15760 iterations

## Conclusões

- A busca em profundidade com poda se mostrou mais eficiente que a busca em profundidade sem poda
- A busca em largura se mostrou mais eficiente que a busca em profundidade, tanto com poda quanto sem poda

# Busca bidirecional

Foi necessário criar uma função a mais na classe dos Nodos para incluir a geração de estados em retrospectiva (*backtrack*). Ou seja, poder gerar os estados a partir do estado final, até o estado inicial.

## Solver sem poda com matriz 4x4

Iterações: 38

## Solver com poda com matriz 4x4

Iterações: 38

## Solver com poda para todos os campos

- Field 1: 38 iterations
- Field 2: 188 iterations
- Field 3: No solution found
- Field 4: No solution found

## Conclusões

- A busca bidirecional se mostrou mais eficiente que a busca em largura e a busca em profundidade para os dois primeros campos, tanto com poda quanto sem poda
- A busca bidirecional não conseguiu encontrar solução para os campos 3 e 4, mesmo com poda
- O algoritmo da busca bidirecional necessita que seja indicada a posição final do Pacman, sendo configurado, nesse caso, como a posição (0,0) do campo. Porém, a escolha dessa última posição afeta o número de movimentos finais, assim, sendo necessário encontrar uma forma automática de encontrar a melhor posição final para o Pacman
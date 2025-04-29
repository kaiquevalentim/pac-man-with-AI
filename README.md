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
- Field 5: 171718 iterations

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

Iterações: 77

## Solver com poda com matriz 4x4

Iterações: 38

## Solver com poda para todos os campos

- Field 1: 38 iterations
- Field 2: 205 iterations
- Field 3: No solution found
- Field 4: No solution found

## Conclusões

- A busca bidirecional se mostrou mais eficiente que a busca em largura e a busca em profundidade para os dois primeros campos, tanto com poda quanto sem poda
- A busca bidirecional não conseguiu encontrar solução para os campos 3 e 4, mesmo com poda
- O algoritmo da busca bidirecional necessita que seja indicada a posição final do Pacman, sendo configurado, nesse caso, como a posição (0,0) do campo. Porém, a escolha dessa última posição afeta o número de movimentos finais, assim, sendo necessário encontrar uma forma automática de encontrar a melhor posição final para o Pacman

# Busca A*

## Explicação da heurística

O algoritmo apresentado é uma variação da busca A* que utiliza uma heurística baseada na distância até a fruta mais próxima, somada à profundidade atual do nó (ou seja, o número de movimentos já realizados). Essa heurística tem como objetivo guiar o Pacman de forma eficiente em direção ao objetivo (comer todas as frutas no mapa), priorizando caminhos promissores sem explorar o estado inteiro do espaço de busca.

Apesar de utilizar uma heurística inspirada na A*, o algoritmo foi intencionalmente ajustado para se comportar de forma mais próxima de uma busca em profundidade. Isso é feito ao inserir os nós filhos ordenados no início da fronteira, em vez de manter uma fila de prioridade ou reordenar toda a fronteira a cada iteração. Essa escolha permite que o algoritmo siga uma trajetória contínua (mantendo a direção), o que reduz drasticamente o número de estados explorados.

- **Vantagem**

O algoritmo reduz significativamente o número de iterações em comparação com versões tradicionais de A*, Busca em largura ou Busca em Profundidade puros. Por exemplo, enquanto outras estratégias podem exigir centenas ou milhares de iterações, esta abordagem pode encontrar uma solução em poucas dezenas.

- **Limitação**

Como os nós não são reinseridos ou reavaliados caso uma nova trajetória mais curta seja descoberta posteriormente, e como o algoritmo prioriza a continuidade da trajetória em vez do custo global mínimo, ele pode encontrar uma solução viável, mas não ótima (ou seja, pode não ser o caminho mais curto possível).

## Solver sem poda com matriz 4x4

Iterações: não conseguiu completar

## Solver com poda com matriz 4x4

Iterações: 45

## Solver com poda para todos os campos

- Field 1: 45 iterations
- Field 2: 52 iterations
- Field 3: 70 iterations
- Field 4: 115 iterations
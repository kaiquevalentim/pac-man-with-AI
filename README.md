# CSP Problems

## Problem 1

**Enunciado:**
Os organizadores de um um evento acadˆemico reservaram 3 salas por 2 dias. O evento tem 11 sessões
técnicas de meio-dia cada, identificadas por letras A,
B, ..., K. As sessões AJ não podem acontecer simultaneamente, assim como JI, IE, CF, FG, DH, BD, KE,
BIHG, AGE, BHK, ABCH e DFJ. Além disso, a sessão
E deve preceder a sessão J, e as sessões D e F devem
preceder a sessão K. A sessão A deve ser alocada no
inicio do primeiro dia e a sessão J no final do segundo
dia. A tarde do segundo dia deve incluir 2 sessões. O
problema é indicar quando e onde ocorrem as sessões
do evento

### Resolução

#### Definições

- **Sessões**: A até K (11 no total)
- **Domínio das variáveis**: Cada sessão é alocada a uma tupla (dia, turno, sala), sendo:
  - Dias: 1 ou 2
  - Turnos: manhã ou tarde
  - Salas: 1, 2 ou 3
  - Total de slots possíveis: 12

#### Restrições

- **Não simultaneidade**: Algumas sessões não podem ocorrer no mesmo turno (ex: A e J, J e I, etc.)
- **Precedência**: Certas sessões devem ocorrer antes de outras (ex: E antes de J)
- **Fixação de horários**:
  - A → dia 1, manhã
  - J → dia 2, tarde
- **Limite de sessões**: Exatamente 2 sessões devem ocorrer na tarde do segundo dia
- **Exclusividade de sala**: Nenhuma sala pode ser usada por mais de uma sessão ao mesmo tempo

#### Resultado

| Sessão | Dia | Turno | Sala   |
|--------|-----|--------|--------|
| A      | 1   | M      | Sala1 |
| B      | 1   | T      | Sala1 |
| C      | 2   | M      | Sala1 |
| D      | 1   | M      | Sala2 |
| E      | 1   | T      | Sala2 |
| F      | 1   | T      | Sala3 |
| G      | 2   | M      | Sala2 |
| H      | 2   | T      | Sala1 |
| I      | 1   | M      | Sala3 |
| J      | 2   | T      | Sala2 |
| K      | 2   | M      | Sala3 |

## Problem 2

**Enunciado:**
O problema “jobshop” consiste no escalonamento de um número de tarefas de um trabalho em um conjunto de máquinas disponíveis. Por exemplo, considerando a tabela 1 (figura \ref{jobshop}), o trabalho 1 tem 5 tarefas, a primeira tarefa leva 72 horas para ser completada e precisa ser feita na máquina 1. No caso, todos os trabalhos têm 5 tarefas. Também temos 5 máquinas (identificadas por 0, 1, 2, 3, 4). As tarefas de cada trabalho devem ser feitas em sequência. O problema é determinar em que momento cada tarefa deve ser realizada e em qual máquina.

### Resolução

#### Definições

- **Tarefas**: Cada job `j` (de 0 a 9) possui 5 tarefas `k` (de 0 a 4), totalizando 50 variáveis `T_jk`.
- **Domínio**: Cada variável `T_jk` representa o instante de início da tarefa `k` do job `j`, com domínio:
  - `D(T_jk) = {0, ..., H - d_jk}`
  - Onde `d_jk` é a duração da tarefa, e `H` é a soma total de todas as durações (horizonte de tempo).

#### Restrições

- **Não simultaneidade em máquinas**: Se duas tarefas `T_jk` e `T_j'k'` usam a mesma máquina, então:
  - `T_jk + d_jk <= T_j'k'` **ou**
  - `T_j'k' + d_j'k' <= T_jk`
  
- **Precedência entre tarefas do mesmo job**: Para cada job `j` e tarefa `k > 0`:
  - `T_jk >= T_j(k-1) + d_j(k-1)`

#### Resultado

![alt text](image.png)
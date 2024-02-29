
Execução simbolica

É um sistema que percorre todos os caminhos possíveis de um programa para determinar quais entradas (inputs) levam á execução de cada um deles - Jammis Kirschner

- Na execução simbolica é atribuido um valor simbolico ao input, não um valor real (abrir codigo)
- Na execução simbolica, todos os caminhos possiveis são percorridos.
- O problema é que dependendo da complexidade do programa e dos fluxos, avançar por todos os caminhos pode não ser uma tarefa muito fácil, concorda ?


Teste Concreto
- O programa le um valor concreto, ou seja, dado um input é analisada sua saída.
- Só os fluxos que possuem as condições satisfeitas pelo input são executados.
- Consequentemente, a execução concreta mais rápido e sem muita complexidade
- Em compensação não é muito útil para dado um alvo (output) descobrir qual input deve ser fornecido. Esse tipo de execução só vai dizer se input X produz output Y ou não.

**Concolic Testing = Concrete Testing + Symbolic Execution**

Repete até que todos os caminhos sejam cobertos
- Executa o programa com um input i "semente" (aleatorio)
- Coleta as restrições (condições) simbóliccas de uma determinada ramificação R
- Inverte a condição para atingir uma nova ramificação
- Encontra uma solução que satisfaça a condição
- Executa novamente com esse novo input i
- Verifica se esse novo input realmente causou a execução da nova ramificação. Caso contrário chamamos de execução divergente
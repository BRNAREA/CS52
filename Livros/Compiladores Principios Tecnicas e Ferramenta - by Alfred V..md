#  Introdução a compilação
## ¹.¹ Compiladores
De formas simples : é um programa que lê outros programas escrito em uma linguagem fonte e o traduz num programa equivalente a outra linguagem a linguagem alvo.

Os compiladores são algumas vezes classificados como de uma passagem , de passagem múltiplas , de carregar e executar , depuradores ou otimizantes 

![[Pasted image 20220711124615.png]]

## O modo de compilação de Análise e Síntese 

Existem duas partes na compilação : a _Análise_ e a _Síntese_ . 

A parte de análise divide o programa  fonte nas partes constituentes e cria uma representação intermedíaria do mesmo . 

A parte de síntese constrói o programa alvo desejado , a partir de representação intermediária .

Durante a análise , as operações implicadas pelo programa fonte são determinadas e registradas numa estrutura hierárquica , chamada de árvore . Frequentemente , é utilizado um tipo especial de árvore , chamado de árvore sintática , na qual cada nó representa uma operação e o filho de um nó representa o argumento da operação.
![[Pasted image 20220711125907.png]]

### O contexto de um compilador 

Adicionalmente ao compilador , varíos outros programas . Um programa fonte pode ser dividido em módulos armazenados em arquivos separados. A tarefa de coletar esses módulos é , algumas vezes confiada a programas distintos , chamado de pré-processor.

O pré-processor pode também expandir formas curtas , chamadas de macros , em enunciados da linguagem fonte.


<h1> ANÁLISE DO PROGRAMA FONTE</h1>
Na compilação a análise consiste em três fases : 

1 - _Análise linear_ ou _Análise léxica_, na qual um fluxo de caracteres constituindo um programa é lido da esquerda para a direita e agrupado em _tokens_ , que são sequencias de caracteres tendo um signifcado coletivo.

2 - _Análise hierárquica_ , na qual os caracteres ou _tokens_ são agrupados hierarquicamente em coleções aninhadas com significado coletivo.

3 - _Análise semântica_ , na qual certas verificações são realizadas a fim de se assegurar que os componentes de um programa se combinam de forma significativa.

![[Pasted image 20220713123446.png]]


##### Análise Léxica

Num compilador , a análise linear é chamada de _Análise Léxica_ ou enquadrinhamento (scaning) . Por exemplo , na análise léxica os caracteres no enunciado de atribuição.

![[Pasted image 20220713130655.png]]


##### Análise sintática

A análise hierárquica é chamada de _Análise Sintática_ . Envolve os agrupamentos dos _tokens_ do programa fonte em frases gramaticais , que são usadas pelo compilador , a fim de sintetizar a saída . 



























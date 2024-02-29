

```ad-info
title: Oque são registradores

# Registradores

Registradores são um tipo de mémoria que ficam dentro da própria CPU.

Os registradores armazenam poucos bits.
Normalmente possuem o mesmo tamanho da palavra de seu processador. Por exemplo, um processador 64bits vai possuir registradores 64bits (alguns registradores especificos permitem acessar parte deles).
```  

<h1 align="center">Registrador de proposito geral</h1>


Existe um conceito chamado **Mapeamento de registradores gerais** onde basicamente serve para aumentar a versatilidade dos usos dos registradores e para poder manipular dados e tamanhos variados no mesmo espaço de memoria dos registradores.

Alguns registradores são divididos em registradores menores e no caso isso seria o mapeamento dos mesmos, que faz com que varios registradores de tamanhos diferentes compartilhem o mesmo espaço , nos primordios da computação a arquitetura **x86** os registradores tinham o tamanho de 16 bits com 2 bytes e posteriormente os processadores aumentaram o tamanho dos registradores para acompanhar a largura do barramento interno de 32bits 4bytes.


AX - Acumulator , serve para operaçoes aritimeticas para armazenar algum calculo.
BX - Serial Base- Usado para endereçamento de mémoria para se referir ao endereço inicial
CX - Counter - Usado para instruções de repetições de código (loops) para controlar o numero de repetições limite.
DX - Serial Data - Usado em Operações de entrada e saída por portas fisicas para armazenar o dado enviado/recebido


```ad-hint
title: ## Nomenclatura

Voce ja reparou que o assembly possui uma ordem alfabetica ? AX , BX, CX, DX , etc..
O sufixo "X" serve para mapear todo registrador enquanto o sufixo "H" mapea o "Higher Bit" e o sufixo "L" mapea o "Lower Bit"

Se alterarmos "AL" o Lower Bit , alteramos o Bit menos significativo de "AX" , o mesmo serve para "AH" onde alteramos o bit mais significativo de "AX" consquetemente do "EAX" e "RAX"
```  


Podem ser usados para desempenhar várias funções
Podem ser usados para armazenar dados ou endereços
Em Algumas arquiteturas eles podem ser dedicadas a uma tarefa especifica.

![[MIPbancoregistarm7.png]]



```ad-question
title: ## Registradores de proposito geral: prós e contras 

# Qual o limite entre definir o registradores de proposito geral ou especifico ?

- Propósito especifico: a execução de operação busca o registrador especifico, sendo necessario somente definir qual o registrador especifico
- Não existe a melhor solução
```  


Nome Alias Desc:

r0 | rax | uma especie de acumulador, usando operações aritimeticas;
r1  | rcx | usado para ciclos (ex: loops)
r2 | rdx | Armazena dados durante operações de entrada e saída
r3 | rbx | Registrador base. Era usado para endereçamento de base nos primeiros modelos de processador
r4 | rsp | Armazena o endereco do elemento do topo da pilha de hardware.
r5 | rbp | Base do stack frame.
r6 | rsi | Indice de origem em comando de manipulação de strings (ex: movsd)
r7 | rdi | Indice de destino em comandos de manipulação de strings (ex movsd)
r8 |
r9 | Não ha | Surgiram dps. Usado principalmente para armazenar variaveis temporarias (as vezes, porem, sao usados implicitamente, como r10, que salva as flags da CPU quando a instrução syscall é executada)


```ad-attention
Em geral, não devemos utlizar os registradores rsp e rbp porque eles impactam diretamente na pilha e stack frame. Mas como podemos executar operações aritimeticas diretamente neles, eles são considerados de próposito geral.
```   

ESP -> APONTA PARA O TOPO DA PILHA
EBP -> APONTA PARA BASE DA PILHA
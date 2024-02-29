1 - Carry Flag (CE)
2 - Zero Flag (ZE)
3 - Sign Flag (SF)
4 - Overflow Flag (OF)

![[Pasted image 20240224164319.png]]

<h1 align="center"> CARRY FLAG (CF)</h1>

```ad-info
title: carry flags

Para causar uma "carry flag" em Assembly, você precisa realizar uma operação que ultrapasse o limite máximo que o registrador pode armazenar. A carry flag é um bit no registro de status do processador que indica quando uma operação aritmética em números inteiros gera um carry out (ou borrow into, no caso de subtração) que excede o tamanho do registrador. Aqui estão algumas maneiras de causar uma carry flag em Assembly, dependendo da arquitetura do processador (x86, ARM, etc.):

Indica se a operação lógica ou aritmetica resultou em uma Carry, ou seja "vai um" no bit mais significativo. (Significa que ocorreu um Overflow de um valor sem sinal)

CF = 0 quando o resultado da última operação não resultou em Carry (vai um)
CF = 1 quando o resultado da última operação resultou em Carry (vai um)
```

<h1 align="center"> ZERO FLAG (ZF)</h1>
```ad-info
title: zero flags

ZF = 1 quando o resultado da última operação lógica ou artimética for zero.
ZF = 0 quando o resultado da última operação lógica ou aritimética for diferente de zero
```


<h1 align="center"> SIGN FLAGS (SF)</h1>
```ad-info
title: sign flags

SETADO para o memso valor do bit mais significativo do resultado

SF=1 valor negativo
SF=0 valor positivo

Testar a flag SF logo após a operação.
Ex: 
ADD RAX, RBX
js LABEL // salta se SF = 1, ou seja, se número negativo.
```  


<h1 align="center"> OVERFLOW FLAG (SF)</h1>

```ad-info
title: overflow flags

OF = 1 quando ocorre overflow com sinal
OF = 0 quando não há um overflow com sinal
``` 
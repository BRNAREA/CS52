
Como o compilador vai lidar com a chamada de uma funcao.
- Define como os argumentos sao passados para a funcao
- Como a funcao que foi chamada retorna para o resultado
- Quem fica responsavel por limpar os parametros da pilha (caller ou callee)

## Fastcall
- o retorno da funcao vai em EAX
- o callee (funcao chamada) fica responsavel  por limpar a pilha
- os 2 primeiros argumentos são passados para os registradores e não á pilha e vão  em ecx e edx respectivamente.
- E os demais argumentos são passados na pilha da direita para esquerda
- O acesso aos registradores são muito mais rápido do que a memoria.

## CDECL : C Declaration

- o retorno da função é passado pelo registrador EAX
- os argumentos são passados pela pilha da direita para a esquerda
- O caller (quem chamou) fica responsavel por limpar a pilha

## STDCALL: Standard Call


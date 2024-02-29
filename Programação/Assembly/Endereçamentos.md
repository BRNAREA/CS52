
## Oque são endereçamentos ?

```ad-info
title: Oque são endereçementos

# Endereçementos

São as formas que a gente vai acessar/trabalhar com os dados seja endereços de mémoria , registradores , atruibuir constatntes e valores a um endereço na memoria, copiar um valor de um registrador para outro, escrever x bytes a partir de uma posição na memoria (indices) etc..
```  


<h2 align="center">Endereçamento direto e relativo</h2>
mov al, 0x22 ; IMEDIATO

mov rsi, rax  ; DIRETO (por registrador)

mov rsi, [rax]

mov rsi, [message]

lea mov -> lead(load effective address) -> carregar o endereco efetivo

lea rsi, [rax] -> nesse caso, mesca coisa de mov rsi, rax

mov rsi, [message + rax] ; copia conteudo da memoria comecando em message+rax (copia 8 bytes)

lea rsi, [message +rax]
mov rsi, message
add rsi, rax





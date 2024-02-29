# Event Loop em JavaScript

> [!INFO] Nota: Este artigo é sobre o Event Loop em JavaScript. Se você não estiver familiarizado com a linguagem JavaScript, recomenda-se que você primeiro estude seus conceitos básicos.

**O Event Loop é um mecanismo fundamental da linguagem de programação JavaScript que permite que o código seja executado de forma assíncrona, sem bloquear a thread principal do navegador. Isso permite que o JavaScript lide com várias tarefas simultaneamente, como processamento de eventos do usuário, comunicação com o servidor e animações.

## Como funciona o Event Loop

O Event Loop é composto por duas partes: a Pilha de Chamadas de Função (Call Stack) e a Fila de Eventos (Event Queue).

> [!SUCCESS] Exemplo:


```js
console.log('1');
setTimeout(() => {   console.log('2'); }, 0); 
console.log('3');
``` 

Nesse exemplo, o primeiro `console.log('1')` será executado imediatamente, e o segundo `console.log('3')` também será executado em seguida. No entanto, o `setTimeout` com um atraso de 0 milissegundos adicionará uma função para ser executada à Fila de Eventos, em vez de ser executada imediatamente. Quando a Pilha de Chamadas de Função estiver vazia, a função adicionada à Fila de Eventos será movida para a Pilha de Chamadas de Função e executada. Portanto, o `console.log('2')` será impresso após o `console.log('3')`, mesmo que tenha sido definido para ser executado após 0 milissegundos.

A Pilha de Chamadas de Função é onde todas as funções são armazenadas enquanto estão em execução. Quando uma função é chamada, ela é adicionada à Pilha de Chamadas de Função. Quando a função é concluída, ela é removida da Pilha de Chamadas de Função.

A Fila de Eventos é onde todos os eventos assíncronos são armazenados. Quando um evento é acionado, ele é adicionado à Fila de Eventos. Quando a Pilha de Chamadas de Função está vazia, o próximo evento da Fila de Eventos é movido para a Pilha de Chamadas de Função e começa a ser executado

## Blocking 

Se tivermos um código assíncrono em JavaScript, como o `setTimeout`, e a call stack do JavaScript nunca ficar vazia, isso pode levar a um problema chamado de "blocking", onde o código assíncrono não será executado até que a call stack esteja vazia.

Isso ocorre porque o Event Loop, que é responsável por verificar a Fila de Eventos e mover os eventos para a Pilha de Chamadas de Função, só pode funcionar quando a Pilha de Chamadas de Função está vazia. Se a Pilha de Chamadas de Função nunca ficar vazia, o Event Loop nunca será executado e os eventos assíncronos nunca serão tratados.

Aqui está um exemplo de como isso pode acontecer:


```js
console.log("Inicio");
setTimeout(function () {   console.log("Evento assíncrono"); }, 0);  while (true) {   console.log("Loop infinito"); }
```

Nesse exemplo, o `setTimeout` é definido para 0 milissegundos, mas nunca será executado porque há um loop infinito logo em seguida. Como a Pilha de Chamadas de Função nunca fica vazia devido ao loop infinito, o Event Loop não pode verificar a Fila de Eventos e executar o evento assíncrono.

Para evitar esse problema, é importante garantir que a Pilha de Chamadas de Função seja mantida o mais curta possível e que eventos assíncronos sejam usados sempre que possível. Além disso, loops infinitos devem ser evitados ou usados com cuidado para não bloquear o Event Loop.

## Conclusão

O Event Loop é um conceito fundamental para entender como o JavaScript funciona de forma assíncrona e como ele lida com várias tarefas simultaneamente. É importante entender como a Pilha de Chamadas de Função e a Fila de Eventos trabalham juntas para permitir que o JavaScript seja executado de forma assíncrona.

> [!WARNING] Atenção: o uso incorreto do Event Loop pode levar a erros e problemas como "blocking" e de desempenho em seu código. Portanto, é importante entender completamente como ele funciona antes de usá-lo em seus projetos. 


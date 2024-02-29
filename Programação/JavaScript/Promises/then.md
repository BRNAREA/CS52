#### .then em Promise

A propriedade ``.then`` usada nas [[Promises]] funcionam basicamente para fazer alguma ação caso a Promise tenha retornado _FULLFILED_ ou seja ; caso a função protótipa tenha conseguido resolver a expressão e recebeu da Promise uma resposta de "OK".

Em seu argumento recebendo uma função para pegar essa "expressão resolvida" , podendo fazer a manipulação dessa resposta.

Exemplo : 

```
	promise.then(function(result) {
		console.log(result);  // "FUNCIONOU !"
	})
```
Não só de 200 vive o código , para capturar o error basta pega-lo com o método [[catch]]. <-
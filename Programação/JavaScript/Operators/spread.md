<h1>O operador spread</h1>

Explicação¹  - Permite que um objeto iterável , como uma expressão de array ou uma string seja expandido para ser usado onde zero ou mais argumentos (para chamadas de funções ) ou elementos (para arrays literais) são esperados , ou que um objeto seja expandido onde zero ou mais pares propriedades:valor (para objetos literais)são esperados.

---
Explicação² - Permite expandir uma expressão em um local que recebe múltiplos argumentos ou elementos.

---
### Na prática
###### Spread na chamada de função

Considere dois valores que precisam ser somados por uma função simples : utilizando o operador spread podemos fazer
esta tarefa sem que seja necessario atribuir os valores deste `Array` a uma variável.

```javascript
	const soma = (a,b) => a+b
	const valores = [40,50];

	console.log(soma(...valores)); // saída 90
```

##### Exemplo 2

Podemos utilizar o operador spread para concatenar dois `Arrays` como abaixo:

```javascript
	const primeiroItens = [1,2,3];
	const outrosItens = [...primeiroItens ,4,5,6];
	console.log(outrosItens) // [1,2,3,4,6]
```

##### Exemplo 4: Spread em uma função

No exemplo abaixo utilizamos o spread em uma função que efetua a soma de todos os argumentos que receber.

```javascript 
	function soma(a,b) {
	return Object.values(arguments).reduce((a,b) => a+b , 0)
	}
	const items = [5,10,1,6,8];
	console.log(soma(...items))
```

Perceba na __linha 5__ que o Array é passado como parâmetro sendo precedido por uma reticencias, isso significa que seus valores serão alocados em cada __ARGUMENTO__ da função.


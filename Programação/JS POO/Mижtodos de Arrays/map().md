#            Método map()

__Nesta documentação de JavaScript conhecermos o método__ `map()` , __do objeto Array__ , que nos permite percorre um vetor e obter um novo array cujo itens são o resultado de uma função de callback que recebe como parâmetro cada item original. Por exemplo , podemos partir de um array de valores numéricos e obter um novo contendo o quadrado de cada item original.

Vejamos

## JavaScript Map na prática

```javascript
	var numeros = [1,2,3,4,5]; // vetor original

	var quadrados = numeros.map(function(item) {
		return Math.pow(item, 2); // retorna o item original 
                                       elevado ao quadrado
	});
	console.log(quadrados) // imprime 1,4,9,16,25
```

## Como funciona o map() ? 

O método `map()` é invocado a partir de um array e recebe como parâmetro uma função de callback , que é invocada para cada item e retorna o valor do item equivalente no array resultante. No exemplo acima , por exemplo , essa função callback retorna o número original ao quadrado.

![[Pasted image 20220727224818.png]]

> [! IMPORTANT ]
> Aqui é importante destacar que o método `map()` não modifica o array original , ele retorna um novo array com os itens resultantes do mapeamento.

### Sintaxe 
```javascript 
arrayOriginal.map(callback);
```

### Parâmetros
`callback` é uma função que será executada para cada elemento no vetor original e retornará uma representação dele com base em alguma lógica , que será o item equivalente no vetor resultante . Sua estrutura é a seguinte.

```javascript
function( valorAtual, indice, array )
```

- O parâmetro `valorAtual` é obrigatório e representa o próprio item da iteração atual. Ou seja , à medida que a função map itera sobre o array , esse parâmetro receberá cada item.
 
- O parâmetro `indice` é opcional e representa o índice do item da iteração atual.

- O parâmetro array também é opcional e representa o array ao qual os itens pertencem.

### Valor de retorno
É retornado um novo array cujos itens são uma representação dos elementos do array original.

## Exemplos de uso do método map()

Exemplo 1
No exemplo a seguir mapeamos um array de objetos e retornamos apenas uma propriedade de cada item:

```javascript
	var vencedores = [
	{
		nome: 'Equipe Super',
		pais: 'Brasil'
	},
	{
		nome: 'Time Maximo',
		pais: 'EUA'
	},
	{
		nome: 'Mega Grupo',
		pais: 'Canada'
	}
];
var podioPorPais = vencedores.map(function(item, indice) {
	return item.pais
});
	console.log(podioPorPais);
```

Exemplo 2
Neste segundo exemplo partiremos do mesmo array visto no exemplo anterior, mas exibiremos os dados das equipes vencedoras em uma tabela . Para isso haverá um elemento table na página com a seguinte estrutura:
```html
<table id="tbPodio">
	<thead>
		<tr>
			<th>Posição</th>
			<th>Nome</th>
			<th>País</th>
		</tr>
	</thead>
</table>
```

Em seguida podemos percorrer o array de vencedores e obter , para cada item , sua representação já na forma de uma linha de tabela:

```javascript
	var vencedores = [
	{
		nome: 'Equipe Super',
		pais: 'Brasil'
	},
	{
		nome: 'Time Maximo',
		pais: 'EUA'
	},
	{
		nome: 'Mega Grupo',
		pais: 'Canada'
	}
];
var podioPorPais = vencedores.map(function(item, indice) {
	return `<tr>
				<td>${indice + 1}</td>
				<td>${item.nome}</td>
				<td>${item.pais}</td>
			</tr>`
});
	document.querySelector("#tbPodio thead").innerHTML = podioPorPais.join("");
```

Exemplo 3

Neste exemplo temos um array de produtos com seus respectivos preços de venda e desejamos simular a aplicação de um reajuste em todos os preços , mas sem modificar a informação original.

```javascript
var produtos = [
{
	nome: 'Smartphone 5 Android',
	preco: 1200
},
{
	nome: 'Notebook 4GB Windows 10',
	preco: 2100
},
{
		nome: 'SmartTV 50 LED',
		preco: 8700
}
];
	var produtosComReajuste = produtos.map(function(item) {
		return {nome: item.nome,
				preco: item.preco
				}
	});
	prodtuosComReajuste.forEach(function(item) {
		console.log(`${item.nome.padEnd(10)} - ${item.preco.toLocaleString("pt-BR", {
		style:"currency", currency: "BRL"
		})}`);
	})
```


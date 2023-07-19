## Retorno de valores com Object.values


O método do objeto `Object.values()` , nos retorna sempre um array com os valores enumerados e com ordem que foram passadas para ele. 

Um exemplo de funcionamento desse cara você pode ver no 
operador da seção - [[spread]] .

##### Exemplo

```javascript
	const animals = {
		camel: 2,
		llama: 3,
		alpace: 13
	}
console.log(Object.values(animal).reduce((a,b) => a+b, 0)
```
# Atribuição via desestruturação
## Desctructuring assignment

A sintaxe de atribuição de **desestruturação** é uma expressão JavaScript que possibilita extrair dados de arrays ou objetos em váriaveis ou objetos em váriaveis distintas

Exemplo ¹

```javascript
function handleScroll(event) {
	const {clientX, clientY} = event;
	console.log(clientX, clientY);
}
window.addEventListener("mousemove", handleScroll)
```

Exemplo ²

```javascript
	function handleScroll({clientX, clientY}){
		console.log(clientX, clientY);
	}
window.addEventListener("mousemove", handleScroll);
```
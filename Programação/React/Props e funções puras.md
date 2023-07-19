Uma função pura

```js
	function sum(a, b) {
		return a + b
	}
```

- A função recebe duas proprieades a e b
- A função não altera o valor das entradas
- Sempre retorna o mesmo resultado para os mesmos tipos de entradas

Uma função impura
	```js
	    function withdraw(account, amount) {
		    account.total -= amount
	    }
	```

- A função altera o valor de sua entrada


>[!WARNING]
>Única regra estrita do React
>
> Todos os componentes React tem que agir como funções puras em relação ao seus props.





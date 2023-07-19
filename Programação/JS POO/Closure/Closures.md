#                   Closures

¹ _Closure_ é quando uma função consegue lembrar e acessar seu escopo léxico mesmo quando está sendo executada fora dele.

O escopo é definido no momento de criação e preservado na compilação , o que significa que a função _bar_ definida dentro de uma função _foo_ vai ter acesso ao escopo externo de foo . E foo será o escopo léxico para _bar_.
```javascript
	function foo() { // escopo léxico para bar
		var memory = 'isto é closure';
		return function bar() {
			console.log(memory);
		}
	}
	var memory = null,
	baz = foo();
	baz(); // 'isto é closure'
```

² Um _closure_ (fechamento) é uma função que se "lembra" ambiente - ou escopo léxico em que ela foi criada.

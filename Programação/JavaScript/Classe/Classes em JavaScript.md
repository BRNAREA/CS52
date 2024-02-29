#         Classes em Javascript

###### Introdução
O JavaScript é uma linguagem baseada em protótipo , e cada objeto no JavaScript tem uma propriedade interna escondida chamada `Prototype` , que pode ser usada para estender as proprieades e métodos de objetos .

##### Classes são funções
¹ Uma classe do Javascript é um tipo de função. As classes são declaradas com a palavra-cheave `class`. Vamos usar a sintaxe de expressão de função para inicializar uma classe.

² Classe é uma estutura que descreve estados e comportamentos de um determinado objeto. Temos duas formas de criar métodos para nossa Classe. Utilizando o <u>prototype</u> que é um recurso do JavaScript que possibilita modificar uma classe depois de que ele foi criada , e outra forma é criar uma função dentro da classe.

³ As Classes são uma das formas de você criar vários objetos com as mesma proprieades , elas vão evitar que você ter que digitar manualmente as proprieades e métodos de cada objeto deve ter.

São basicamente " funções especiais " que constroem novos objetos. 
Classes podem ou não ser nomeadas e ser atribuidas à uma variável ou você pode retornar uma classe dentro de uma função

```javascript
	// Inicializa uma função com uma expressão de function
	const x = function() {}

	//Inicializa uma classe com uma expressão de classe
	const y = class {}
```

Ambos os códigos declarados com `function` e `class` retornam uma função `Prototype` .

Com protótipos , qualquer função pode ser tornar uma instância de construção usando a palavra-chave `new`

```javascript
const x = function() {}

// Initialize a constructor from a function
const constructorFromFunction = new x();

console.log(constructorFromFunction);
```

Isso também se aplica às classes. 

```javascript
const y = class {}

// Initialize a constructor from a class
const constructorFromClass = new y();

console.log(constructorFromClass);
```

Para criar herança no JavaScript vamos utilizar prototype , vamos transferir proprieades e métodos de um objeto para outro.



## O que é o constructor ?

O "constructor" é um método especial que cria e inicializa um objeto gerado à partir de uma classe. Dentro do constructor , você pode criar as proprieades iniciais que o objeto vai ter.

Quando passamos um argumento e invocamos a classe , esse argumento acontecem duas coisas:

- O novo objeto é criado.
- O parâmetro do constructor recebe o argumento que a gente passou nessa invocação da classe. 



























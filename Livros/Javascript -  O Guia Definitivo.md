# Anotações importantes
>[!SUMMARY]
pt-oplc

>[!INFO]
>Em *JavaScript* a desalocação de memoria é manipulada  automaticamente pela coleta de lixo e nunca é preciso se preocupar em liberar memoria explicitamente.

---
>[!QUESTION]
> __Qual a diferenca entre Javascript e ECMA Script __?

>[!ANSWER]
>O ECMA Script é uma especificacao , contendo diretrizes e regras para padronizar o Javascript , mantida pela comunidade e gerida pela Mozila Foundation. O JavaScript é uma linguagem de script que segue os padroes sugeridos pelo _ECMA Script_

---
>[!QUESTION]
>Qual a diferenca entre valor indefinido e nulo ?

> [!ANSWER]
> Um valor `undefined` significa que uma variavel foi declarada , mas ainda não foi atribuido um valor , ja um valor nulo é um valor atribuido ou resultado de um erro gerado.
> As variaveis no JavaScript quando inicializadas e nao atribuidas tem em seu valor por padrao `undefined`

---
>[!QUESTION]
>O que é uma `closure` no _Javascript?_

>[!ANSWER]
>`Closures` são variáveis ou funções que fazem parte do escopo de uma função , possuem acesso limitado ao escopo da função a que pertencem.

---
>[!QUESTION]
>Como voce pode lancar exceções manualmente no *JavaScript* ?

>[!ANSWER]
>Usando a declaração throw com uma expressao , geralmente uma instancia do constructor Error do JavaScript. Ao  lançar esta exceção a funcao sera interrompida e o retorno sera passado para o primeiro bloco de funcao catch em um try.

---

>[!INFO]
>Objeto -> Conjunto de propriedades , em que cada prorpriedade tem uma Chave e Valor podendo ser um valor primitivo (numero , string , bool , ou um objeto).

>[!INFO]
>O Interpretador Javascript faz a *coleta de lixo* automaticamente para o gerenciamento de memoria. Coisa que em outras linguagens não fazem .

>[!INFO]
>JavaScript é uma linguagem orientada a objetos. Isso significa que, em vez de ter funções definidas globalmente para operar em valores de vários tipos, os próprios tipos definem métodos para trabalhar com valores.

## Lvalue
> [!QUOTE] 
> Lvalue e um termo  historico que significa "*uma expressao que pode aparecer de forma valida no lado esquerdo  de uma expressao de atribuicao*"

	Em javascript VARIAVEIS , PROPRIEDADES DE UM OBJETO ou ELEMENTOS DE ARRAYS sao lvalues


## Operador " in "

O operador __in__ espera no lado esquerdo que seja ou possa ser convertido em uma string. No lado direito , ele espera um operando que seja um objeto . Ele e valido com true se o valordo lado esquerdo for o nome de uma propriedade do objeto do lado direito. Por exemplo

```
	 var point = { x:1, y:1};    // define um objeto
	 "x" in point       // verdadeiro: o objeto tem uma prop 
                            chamada "x"
	
	"z" in point        // falso: o objeto nao tem uma prop 
                         chamada z
	"toString" in point     //verdadeiro: o objeto herda o metodo 
                            toString
```

## Operador " instanceof "

O operador __instanceof__ espera um objeto para o operando no lado esquerdo  e um operando no lado direito que indentifique uma classe de objetos.

O operador e avaliado como __true__ se o objeto do lado esquerdo e uma instancia da classe do lado direito e é avaliado como __false__ caso contrario.

Exemplo:

```
	var d = new Date(); // cria um novo Objeto com a construturora 
                         Date
    
    d instanceof Date;  // true: d foi criado com Date()
    d instanceof Object; // true: todos os objetos sao instancias 
                            de Object
    d instanceof Number; // false: d nao é um objeto Number
    
```
---

__Note que todos os objetos são instâncias de Object__ . instanceof considera as “superclasses” ao decidir se um objeto é uma instância de uma classe. Se o operando do lado esquerdo de instanceof não é um objeto, instanceof retorna false. Se o lado direito não é uma função, ele lança um TypeError. 

Para entender como o operador instanceof funciona, você deve entender o “[[Encadeamento de protótipos]]”. Trata-se de um mecanismo de herança de JavaScript e está descrito na Seção 6.2.2. Para avaliar a expressão o instanceof f, JavaScript avalia f.prototype e depois procura esse valor no "encadeamento de protótipos" de o. Se o encontra, então o é uma instância de f (ou de uma superclasse de f) e o operador retorna true. Se f.prototype não é um dos valores no encadeamento de protótipos de o, então o não é uma instância de f e instanceof retorna false.

Uma deficiência do operador _instanceof_  e do método _isPrototypeOf_ é que eles não nos permitem consultar a classe de um objeto , mas somente testar um objeto em relação a uma classe que especificamos.
## Instruções rotuladas
Qualquer instrução pode ser rotulada por ser precedida por um **identificador** e dois-pontos:
	``identicador: instrução``

>[!INFO]
>**Rotulando uma instrução , você dá a ela um nome que pode ser usado  para se referir a ela em qualquer parte do seu programa.**

É possivel rotular qualquer instrução , embora só seja util rotular instruções que tenham corpos , como **laços** e **condicionais**. Dando um nome a um laço , você pode usar instruções como ``break`` e ``continue`` dentro do corpo do laço para sair dele ou para pular diretamente o seu início , a fim de começar  a próxima iteração.

**Exemplo de um laço rotulado e de uma instrução continue que utiliza o rótulo : **
````
	mainloop: while(token != null ) {
		//Codigo omitido...
		
		continue mainloop;  // Pula para proxima iteração do laço nomeado.
		
		// Mais um codigo omitido..
	}
````
Os  rótulos  de instrução são definidos **SOMENTE DENTRO DA INSTRUÇÃO NA QUAL SÃO APLICADOS (*e dentro das suas subinstruções evidentemente*).

---
## Break e instruções com rótulo

O JavaScript também permite que a palavra-chave ``break`` seja seguida por um rótulo de instrução. Quando a instrução ``break`` é usada com um rótulo , ela pula para o final (ou termina) da instrução circundamente que tem o rótulo especificado . Se não houver qualquer instrução circundamente com o rótulo especificado , é um erro de sintaxe usar ``break`` dessa forma .

#### !IMPORTANTE
A forma rotulada da instrução ``break`` é necessaria quando se quer sair 
de uma instrução que não é o laço ou uma instrução switch circundamente mais próxima. O código a seguir demonstra isso : 

```
	var matrix =  getData();  // Pega um array 2D de algum lugar
	// agora soma todos os numeros da matriz.
	var sum = 0, success = false;
	
	// Começa com uma instrução rotulada da qual podemos sair se ocorrerem erros
	
	compute_sum: if (matrix){
		for(var x = 0; x < matrix.length; x++) {
			var row = matrix[x];
			if (!row) break compute_sum;

		for(var y = 0; y < row.length; y++){
			var cell = row[y];
			if (isNaN(cell)) break compute_sum;
			sum += cell;
		}
	}
	success = true;
}

/// As instruções break pulam pra cá . Se chegarmos squi com success = false, entao algo deu errado com a matriz que recebmos.
//Caso contrário , sum contém a soma de todas as células de matriz
```
---
## Return
	Lembre-se de que as chamadas de funções são expressões e de que todas as expressões têm valores.

Uma instrução return dentro de uma função especifica o valor das chamadas dessa função. Vamos fazer a sintaxe da expressão return :

	return expressão;

A instrução ``return`` só pode aparecer dentro do corpo de uma função. É erro de sintaxe ela aparecer em qualquer outro lugar. Quando a instrução ``return`` é executada , a função que a contém **retorna** o valor de ***EXPRESSÃO*** para sua chamada. Por exemplo :

	```
	function sqaure (x) {return x*x; } // Uma função que tem instrução return

	square(2) // Esta chamada é avaliada como 4
	```

>[!WARNING]
>**Sem uma instrução return , uma chamada de função simplesmente executa cada uma das instruções do corpo da função até chegar ao fim da função e , então , retorna para sua chamadora. Nesse caso , a expressão de invocação é avaliada como** ``undefined``

Então ja sabemos que uma função retorna para sua chamadora  quando a instrução ``return`` é executada , mesmo que não restem outras instruções no corpo da função.

A instrução ``return`` também pode ser usada sem *expressão* , para a função retornar ``undefined`` para sua chamadora . Por exemplo :

````
	function display_objeto(o){
	//Retorna imediatamente se o argumento for null ou undefined.
	if (!o) return;
	// O resto da função fica aqui...
	}

````
Mas lembre-se tudo que vir depois da instrução ``return`` não será executada , isso deve-se ao fato da inserção automática de ponto e vírgula em *JavaScript*.

---
## throw

Uma *EXCEÇÃO* é um sinal que ocorreu algum tipo de condição execepcional ou erro. *Disparar uma exceção* é sinalizar tal erro ou condição excepcional. *Capturar* uma exceção é tratar dela - executar as ações  necessárias ou apropriadas para se recuperar da exceção .

	Em JavaScript , as exceções são lançadas quando ocorre um erro em tempo de execução e quando o programa lança uma explicitamente , usando a instrução throw.

As exceções são capturadas com a instrução ``try/catch/finally``.

Sintaxe : 
	``throw expressão``

*expressão* pode ser avaliada como um valor de qualquer tipo.

Quando uma exceção é disparada , o interpretador JavaScript interrompe imediatamente a execução normal do programa  e pula para a rotina de tratamento de exeção mais próxima .

As rotinas de tratamento de exceções são escritas usando a cláusula ``catch`` da instrução ``try/catch/finally`` .
### ² classe Error


Um objeto **Error** tem uma propriedade *name* que especifica o tipo de erro e uma propriedade *message* que contém a string passada para função construtora. Aqui está um exemplo  de função  que lança um objeto Error quando chamada com um argumento inválido:

```
	function factorial(x) {
		// Se o argumento de entrada é invalido , dispara uma exceção !

	if (x < 0) throw new Error("x must not be negative");

	// Caso contrario , calcula um valor e retorna normalmente 
	for(var f = 1; x > 1; f *= x, x--) /*vazio*/;
	return f;
	}
```

---
## try/catch/finally

-> São usados para tratamentos de exeções
- O ``try`` testa a função passada.
- O ``catch`` pega as execeções dessa função se houver.
- O ``finally`` é sempre executado independente do que acontece no try.

>[!NOTE]
>Note que a palavra-chave ``catch`` é seguida por um identificador entre parênteses. Esse identificador é como um parâmetro de função. Quando uma exceção é capturada , o valor associado à exceção (um objeto Error, por exemplo ) é atribuido a esse parâmetro .

Exemplo realista  da instrução ``try/catch`` . Ele usa o método factorial() definido na seção anterior e os métodos JavaScript do lado do cliente ``prompt()`` e ``alert()`` para entrada e saída:

```
	try {
		// Pede para o usuario inserir um número
		var n = Number(prompt("Please enter a positive Number" , ""));
		//Calcula o factorial do número , supondo que a entrada seja válida
		var f = factorial(n);
		// Mostra o resultado
		alert(n + "! = " + f);
	}
	catch (ex) {  // Se a entrada não foi valida , terminamos aqui
		alert(ex); // Informa ao usuario qual é o erro
	}
```


# Instruções diversas
Esta seção descreve as três instruções restantes de JavaScript - ``with`` , ``debugger``, e ``use strict``

## with
A instrução ``with`` é usada para ampliar o encadeamento de escopo temporariamente. Ela tem a seguinte sintaxe:

```
	with(objeto)
	instrução
```

Essa instrução adiciona *objeto* na frente do encadeamento de escopo , executa instrução e , então , restaura o encadeamento de escopo ao seu estado original.

>[!WARNING]
>A instrução **with** é proibida no modo restrito e deve ser considerada desaprovada no modo não restrito : evite usá-la , quando possivel.

O uso comum  da instrução ``with`` é para facilitar o trabalho com hierarquias de objeto profundamente aninhadas. 

Em JavaScript do lado do cliente , por exemplo , talvez seja necessario digitar expressões como a seguinte para acessar elementos de um formúlario em HTML.

		``document.forms[0].address.value``

Caso precise escrever expressões como essa varias vezes , você pode usar a instrução ``with`` para adicionar o objeto formulário no encadeamento de escopo:

```
	with(document.forms[0]) {
		// ACESSA OS ELEMENTOS DO FORMULARIO DIRETAMENTE DAQUI.EX:
		name.value = "";
		address.value = "";
		email.value = "";
	}
```

É claro que é muito simples evitar a instrução ``with`` e escrever o código anterior como segue: 

```
	var f = document.forms[0];
	f.name.value = "";
	f.address.value = "";
	f.email.value = "";
```

---
## "use strict"
``use strict`` é uma *diretiva* introduzida em ECMAScript5.
As *diretivas* não são instruções (mas são parecidas o suficiente para que ``use strict``  seja documentada aqui). Existem duas diferenças importantes entre a diretiva ``use strict`` e as instruções normais:

- Ela não inclui qualquer palavra-chave da linguagem : diretiva é apenas uma instrução de expressão que consiste em uma string literal especial (entre aspas simples ou duplas).

- Ela só pode aparecer no ínicio de um _script_ ou no ínicio do corpo de uma função , antes que qualquer instrução real tenha aparecido. Contudo, não precisa ser o primeiro item no script ou na função.

	O objetivo de uma diretiva ``use strict`` é indicar que o codigo a seguir (no script ou função) é um _c o d i g o   r e s t r i t o_ .

	Um codigo restrito é executado no _modo restrito_ . O modo restrito de ECMAScript 5 é um subconjunto restrito da linguagem que corrige algumas deficiências importantes e fornece verificação de erro mais forte e mais segurança.

### Diferenças entre modo restrito e não restrito

**As três primeiras são especialmente importante**.

- A instrução ``with`` não é permitida no modo restrito.

- No modo restrito , todas as varíaveis devem ser declaradas : um ``ReferenceError`` é lançado se você atribui um valor a um identifcador que não é uma varíavel , função , parâmetro de função , parâmetro de cláusula ``catch`` ou propriedade declarada do objeto global. ( No modo não restrito , isso declara uma varíavel global implicitamente , pela adição de uma nova propriedade no objeto global).

- No modo restrito , as funções chamadas como funções (e não como métodos) têm o valor de ``this`` igual a ``undefined`` . (No modo não restrito , as funções chamadas como funções são sempre passadas para o objeto global como seu valor de ``this``) . Essa diferença pode ser usada para determinar se uma implementação suporta o modo restrito :
	- ``var hasStrictMode = (function() { "use strict"; return this === undefined}());``
	- Além disso, no modo restrito, quando uma função é chamada com call() ou apply(), o valor de this é exatamente o valor passado como primeiro argumento para call() ou apply(). (No modo não restrito, valores null e undefined são substituídos pelo objeto global e valores que não são objeto são convertidos em objetos.)

---
<h1>Capitulo 6 </h1>
# Objetos

O tipo fundamental de dados de JavaScript  é o ``objeto`` . Um objeto é um valor composto : ele agrega diversos valores (valores primitivos ou outros objetos) e permite armazenar esses valores pelo nome .

Um objeto é um conjunto não ordenados de _propriedades_ , cada uma das quais tendo um **nome** e um **valor** . Os nomes das propriedades são strings ; portanto , podemos dizer que os objetos mapeiam strings em valores.

Esse mapeamento de string em valor recebe vários nomes : você provavelmente já conhece  a estrutura de dados fundamental pelo nome  ``hash`` , ``tabela de hash`` , ``dicionario`` , ou ``array associativo`` . Contudo , um objeto é mais do que uma simples propriedades , um objeto JavaScript também herda as propriedades de outro objeto , conhecido como seu ``protótipo ou prototype`` . Os métodos  de um objeto normalmente são propriedades herdadas  e essa "herança de protótipos" é um recurso imporante de Javascript.

Os objetos de JavaScript são dinâmicos - normalmente propriedades podem ser adicionadas e excluídas , mas podem ser usados para simular os objetos e as "estruturas" estáticas das linguagens estaticamente tipadas .

- Qualquer valor em JS que não seja uma string  , um número , um booleano , null ou undefined é um objeto . E mesmo que strings , números e valores booleanos não sejam objetos , eles se comportam como objetos imutáveis .

	Lembre-se -> Objetos são _m u t a v e i s_ e são manipulados por referência e não por valor. Se a variavel x se refere a um objeto e codigo e o código ``var y = x;`` é executado , a variável y contém uma referêcia para o mesmo objeto e não uma cópia desse objeto . Qualquer modificação feita no objeto por meio da variável y também é visivel por meio da variável x.

	Uma _propriedade_ tem um **nome** e um **valor** podendo ser um string , incluindo string vazia , mas nenhum objeto pode ter duas propriedades com o mesmo nome.


## Atributos de propriedades

- O atributo _gravavel_ especifica se o valor da propriedade pode ser configurado .
- O atributo _enumeravel_ especifica se o nome da propriedade é retornado por um laço ``for/in``
- O atributo _configuravel_ especifica se a proprieade pode ser excluída e seus atributos podem ser alterados.

>[!INFO]
>Antes de ECMAScript 5, todas as propriedades dos objetos criados por seu código eram graváveis, enumeráveis e configuráveis. Em ECMAScript 5 é possível configurar os atributos de suas propriedades.

Além de suas proprieades , todo objeto tem três _atributos de objeto associados_ :

- O _P R O T O T I P O_ de um objeto é uma referência para outro objeto do qual as propriedades são herdadas .
- A _C L A S S E_ de um objeto é uma string que classifica o tipo de um objeto .
- O flag _E X T E N S I V E L_ de um objeto especifica se novas proprieades podem ser adicionadas no objeto .

<h2> Criando Objetos </h2>
Os Objetos podem ser criados com objetos literais , com a palavra-chave ``new`` e (em ECMAScript 5 )com a função ``Object.create()``

<h3> Objetos Literais </h3>
A maneira mais facil de criar um objeto é incluir um objeto literal no código JavaScript . Um _objeto literal_ é uma lista separada com vírgulas de pares nome:valor separados por dois pontos , colocados entre as chaves.

Exemplos de criação de objetos : 

```
	var empty = {} ; // Um objeto sem propriedade
	var point = { x: 0 , y: 0}; //Duas prop
	var point2 = {x: point.x, y:point.y+1} // Valores Complexos

	var book = {
		"main title": "JavaScripto",
		'sub-title' : "O guia definitivo",
		"for": "todas os publicos",

		author: {
			firstname: "David",
			surname: "Flanagan"
		}
	};
```

Note que os nomes de propriedade incluem espaços e hifens; portanto, usam strings literais

for é uma palavra reservada; portanto, usa aspas

O valor dessa propriedade é ele próprio um objeto. Note que esses nomes de propriedade não têm aspas.

<h3> Criando objetos com new </h3>
O operador ``new`` cria e inicializa um novo Objeto.  A palavra-chave ``new`` deve ser seguida de uma chamada de função. Uma função usada dessa maneira é chamada de _construtora_ e serve para inicializar um objeto recém-criado. Exemplos :

```
	var o = new Object(); //  Cria um objeto vazio: o mesmo que {}
	var a = new Array(); // Cria um Array vazio: o mesmo que [].
	var d = new Date(); // Cria um objeto Date representando a hr
	var r = new RegExp("js"); // Cria um regex para comparar pdrao	
```

<h2>Protótipos</h2>
	Todo objeto JavaScript tem um segundo objeto Javascript (ou ``null`` , mas isso é raro) associado . Esse segundo Objeto é conhecido como _prototipo_ e o primeiro objeto herda proprieades do protótipo.

Todos os objetos criados por objetos literais têm o mesmo objeto protótipo e podemos nos referir a esse objeto protótipo em JS como ``Object.prototype`` . 

``Object.prototype`` é um dos raros objetos que não tem protótipos : ele não herda propriedade alguma. Outros objetos  protótipos são objetos que normais que têm protótipo

<h4> Criando um novo objeto que herda um protótipo </h4>
```
	// inherit() retorna um objeto recem-criado que herda proprieades do objeto prototipo p. Ele usa a funcao ECMAScript 5 Object.create() se estiver definida e caso contrario , retrocede para uma tecnica mais antiga.

	function inherit(p) {
		if(p == null)throw TypeError();
		if(Object.create)
			return Object.create(p);
		var t = typeof p;

	if (t !== "object" && t !== "function") throw TypeError();
	function f() {};
	f.prototype = p;
	return new f();
				// p deve ser um objeto não null 
				// Se Object.create() está definida... 
				// então basta usá-la. // Caso contrário, faz mais alguma verificação de tipo .
				// Define uma função construtora fictícia. // Configura sua propriedade prototype como p.
				// Usa f() para criar um "herdeiro" de p.
	}
```
---
<h2>Métodos getter e setter de proprieades</h2>
>[!INFO]
>Propriedades definidas por métodos getter e setter às vezes são conhecidas como _proprieades de acesso_ , para distingui-las das _proprieades  de dados_ que tem um valor simples.

Quando um programa consulta o valor de uma proprieade de acesso , JavaScript chama o método __getter__ (sem passar args) . O valor de retorno desse método se torna o valor da expressão de acesso a proprieade 

Quando um programa configura o valor de uma prop de acesso , JS chama o método __setter__ , passando o valor do lado direito da atribuição .

A maneira mais fácil de definir uma proprieade de acesso é com uma extensão da sintaxe de objeto literal :

```
	var o = {
		// uma prop de dados normal
		data_prop: value,

		// Uma prop de acesso definida como um par de funcoes
		get_accessor_prop() { /*corpo*/},
		set accessor_prop(value) { /*corpo*/}
	};
```

---
### Definir Propriedades
Para configurar os atributos de uma proprieade ou criar uma nova proprieade com os atributos especificados , chame _Object.definePropertuy()_, passando o objeto a ser modificado , o nome da proprieade a ser criada ou alterada e o objeto descritor de proprieade:

```
	var o = {} // Objeto vazio
	Object.defineProperty(o, "x", { value: 1,
	writable: true,
	enumerable: false,
	configurable: true});

	o.x; // => 1
	Object.keys(o) // => []

	// Agora modifica a prop x para que seja somente leitura
	Õbject.defineProperty(o, "x", {writable: false})

	// Tenta alterar o valor da prop
	o.x = 2; // Falha ou lança um TypeError
	o.x // => 1

	// A prop ainda é configuravel; portanto , podemos alterar seu valor, como segue:

	Object.defineProperty(o, "x", {value: 2});
	o.x // => 2


	// Agora altera x de uma propriedade de dados para uma propriedade de acesso 
	Object.defineProperty(o, "x", { get: function() { return 0; } }); o.x // => 0
```

---
<h1>Atributos de Objeto</h1>
	Todo objeto tem atributos _prototipos, classe e extensivel associados._ As subseções explicam o que esses atributos fazem e (quando possivel) como consulta-los

<h2>O atributo protótipo </h2>
	O atributo _protótipo_ de um objeto especifica o objeto do qual ele herda propriedades. Esse é um atributo tão importante que em geral dizemos simplesmente "o protótipo de o", em vez de "o atributo protótipo de o" . Além disso , é importante entender que quando , quando o _prototype_ aparece no código-fonte , isso se refere a uma proprieade de objeto normal e não ao atributo protótipo

O atributo protótipo é configurado quando um objeto é criado.
objetos criados a partir de objetos literais usam _Object.protype_ como protótipo. 

Objetos criados com _new_ utilizam como protótipo o valor da proprieade _prototype_ de sua função construtora.

Objetos criados com _Object.create()_ usam o primeiro argumento  dessa função (que pode ser ``null`` ) como protótipo.

---

<h2> O atributo extensivel </h2>
O atributo *extensivel* de um objeto especifica se novas proprieades podem ser adicionadas no objeto ou não .

Em ECMAScript 5 **todos** os objetos internos e definidos pelo usuario são extensiveis , a não ser que tenham sido convertidos para serem não extensiveis.

ECMAScript 5 define funções para consultar e configurar a capacidade de extensão de um objeto.

Para determinar se um objeto é extensivel , passe-o para ``Object.isExtensible()`` . 

Para tornar um objeto não extensivel , passe-o para ``Object.preventExtensions()``. Note que uma não ha modo de tornalo extensivel novamente. Use com cuidado 

---
<h1> Serializando Obejtos </h1>
_Serlialização_ de objetos é o processo de converter o estado de um objeto em uma string a partir da qual ele pode ser restaurado posteriormente. 

	ECMAScript 5 fornece as funções nativas JSON.stringfy() e JSON.parse() para serializar e restaurar objetos de JavaScript.

Essas funções utilizam o formato de troca de dados JSON. (JavaSCript Object Notation) sua sintaxe é parecida com a de objetos e array literal .

``` 
	o = {x: 1, y: {z: [false, null, ""]}};
	s = JSON.stringfy(o);
	p = JSON.parse(s);
```

---
<h1> Iteração em arrays </h1>
<h4> A maneira mais comum de iteirar através dos elemntos de um array é com um laço for </h4>
```
	var keys = Objects.keys(o) // Obtém um arr de nomes e prop do objeto o

	var values = []
	for(var i = 0; i < keys.length; i++){ // Para cada indice do 
                                              array
    var key = keys[i]; // Obtém a chave desse indice
    values[i] = o[key]; //Armazena o valor no array values
	}
```

Se quiser excluir elementos ``null , undefined ou inexistentes``  , você pode escrever o seguinte codigo :

```
	for(var i = 0; i < a.length; i++){
		if (!a[i])continue; // Pula elementos null undefined e inexistentes
		resto...
	}
```

<h2>For/In</h2>
>[!IMPORTANT]
>O laço ``for/in`` também pode ser usado com array esparsos . Esse laço atribui nomes de propriedades enumeráveis (incluindo índices de array) á variável de laço , um por vez . Os índices que não existem não são iterados:

```
	for(var index in sparseArray){
		var value = sparseArray[index];
	}
```

A especificação ECMAScript permite que o laço ``for/in`` itere pelas propriedades de um objeto em qualquer ordem . As implementações normalmente iteram nos elementos do array em ordem crescente , mas isso não é garantido .

<h3>forEach</h3>
O laço ``forEach`` e os métodos de iteração relacionados possibilitam um estilo de programação funcional simples e poderoso para se trabalhar com arrays. Esse método é o mais geral dos laços:

```
	var data = [1,2,3,4,5,6,7,8,9,10]; // Este é o array de iterar
	var soma = 0; // Queremos calcular a soma dos quadrados

	data.foreach((data) => {soma += data*data // soma os quadrados}) // Passa por cada elemento de data para essa função
```

---
<h1> Array multidimensionais </h1>
<h4>Na verdade JavaScript não suporta array multidimensionais , mas é possivel ter algo parecido , como array de arrays</h4>
Basta usar o operador [ ] duas vezes .
Suponha que a variável *matrix* seja um array de arrays de números . Todo elemento em matrix[x] é um array de números . Para acessar um número especifico basta escrever matrix[x y] 

>[!SUCCESS]
>Aqui está um exemplo concreto que utiliza array bidimensional como tabuada de multiplicação

```
	var table = new Array(10);
	for(var i = 0; i < table.length; i++) {
		table[i]  new Array(10);

	 //Inicializa o array
	 for(var row = 0; row < table.length; row++) {
		 for(var col = 0; col < table[row].length; col++) {
			 table[row][col] = row*col;
		 }
	 }
	}
```

<h2>Métodos de arrays</h2>
O ECMAScript 3 define várias funções de manipulação úteis em Array.prototype , isso quer dizer que elas estão disponiveis como método de qualquer array .
>[!ATENTION]
>Somente anotarei os mais importantes !
<h3>join()</h3>

O método Array.join() converte todos os elementos de um array em strings e as concatena , retornando a string resultante.
```
	var a = [1, 2, 3]; // Cria um novo array com esses três 
    elementos a.join(); // => "1,2,3" a.join(" "); // => "1 2 3" 
    a.join(""); // => "123" var b = new Array(10); // Um array de 
    comprimento 10 sem elementos b.join('-')
```

<h3>reduce()</h3>
	Esse método combina os elementos de um array usando a função especificada para produzir um valor único.

__reduce()__ recebe dois argumentos . 
- O primeiro é a função que efetua a operação de redução .
- O segundo argumento (opcional) é um valor inicial a ser passado para a função.

<h3>sort()</h3>
O método Array.sort() classifica de um array no local e retorna o array classificado . Quando chamado sem argumentos , ele classifica os elementos do array em __ORDEM ALFABETICA__.

```
	var a = new Array("banana", "morango", "amora");
	a.sort();
	var s = a.join(", "); s == "amora", "banana", "morango"
```

>[!IMPORTANT]
>Para classificar um array diferente da ordem alfabetica , deve se passar uma função de comparação como argumento para sort().
><br>
>	Essa função decide qual de seus dois argumentos deve aparecer primeiro no array classificado.
>	<br>
>	Se o primeiro argumento deve aparecer antes do segundo a função de comparação deve retornar um número menor do que zero .
>	<br>
>	Se o primeiro argumento deve aparecer após o segundo no array classficado , a função deve retornar um número maior do que zero.
>	E se os dois valores são equivalentes (isto é , se a ordem é irrelevante), a função deve retornar 0.


![[Pasted image 20220629141409.png]]


Como outro exemplo de classificação de itens de Array temos , poderia ser feita uma classificação alfabética sem considerar letras maiúsculas e minusculas em um array de strings , passando-se uma função de comparação que convertesse seus dois argumentos em minúsculas (com o método ``toLowerCase()`` antes de compará-los):

```
	a = ['ant', 'Bug', 'cat', 'Dog'];
	a.sort();

	a.sort(function(s,t) {
		var a = s.toLowerCase();
		var b = t.toLowerCase();
		if (a < b) return -1;
		if (a > b) return 1;
		return 0;
	}) // ['ant', 'Bug', 'cat', 'Dog']
```

![[Pasted image 20220629142045.png]]

<h3>push() e pop()</h3>
Os métodos ``push()`` e ``pop()`` permitem trabalhar com arrays como se fossem pilhas

-> push() anexa um ou mais novos elementos no final de um array e retorna o novo comprimento do array.

->pop() exclui o ultimo elemento de um array , decrementa o comprimento do array e __retorna o valor que removeu__ .

Exemplo:

```
	var stack = [];
	stack.push(1,2); // stack: [1,2]retorna 2
	stack.pop(); // stack: [1] retorna 2
	stack.push(3); //stack: [1,3] retorna 2
```

---
<h2> Métodos de Arrays de ECMAScript 5 </h2>
ECMAScript 5 define  nove novos  métodos de array para iterar , mapear, filtrar, testar , reduzir e pesquisar arrays.

### forEach() na prática

Itera por um array , chamando uma função especificada para cada elemento. 

O primeiro argumento conforme descrito é passada uma função com três argumentos: 

- O valor do elemento 
- O indice do elemento
- E o array em sí

```
	var data = [1,2,3,4,5];
	var sum = 0;
	data.forEach(function(value) { sum += value;});
	sum

	Agora incrementa cada elemento do array
	data.forEach(function(v,i,a) {a[i] = v+1;});
	data
	// => [2,3,4,5,6]

```

Note que o foreach() não fornece um método de terminar a iteração antes que todos os elementos tenham sido passados para a função.

Se precisar terminar antes , você deve lançar uma exceção e colocar a chamada forEach() dentro de um bloco try.
![[Pasted image 20220629155418.png]]

### every()
O método ``every()`` é como um quantificador matemático "para todo":

Ele retorna ``true`` se , e somente se , sua função de predicado retorna true para todos os elementos do array:

```
	a = [1,2,3,4,5];
	a.every(function(x) => {return x < 10})// true: valores < 10..
	a.every(function(x) => {return x%2 === 0;})// falso : nem todos valores são pares
	
```

### some()
O método ``some()`` é como o quantificador matemático "existe" : ele retorna true se existe pelo menos um elemento no array para o qual o predicado retorna true , e retorna false se , e somente se , o predicado retorna false para todos os elementos do array;

```
	a = [1,2,3,4,5]; a.some(function(x) { return x%2===0; }) // => verdadeiro: a tem alguns números pares. 
	
	a.some(isNaN) // => falso: a não tem não números.
```
---
<h2>indexOf() & lastIndexOf()</h2>


---
<h1> Capítulo 8 </h1>
<hr>
# Funções

## Argumentos e parâmetros  de função

As definições de função em Javascript não especificam um tipo esperado para os parâmetros e as chamadas de função não fazem qualquer verificação de tipo nos valores de argumento passados.

Na verdade , as chamadas de função em JS nem mesmo verificam o número de argumentos que estão sendo passados .

### Parâmetros opcionais
>[!IMPORTANT]
>Quando uma função é chamada com menos argumentos do que parâmetros adicionais são configurados com o valor ``undefined`` 

Frequentemente é útil escrever funções de modo que alguns argumentos sejam opcionais e possam ser omitidos na chamada da função. Para fazer isso, deve-se atribuir um valor padrão razoável aos parâmetros omitidos. Aqui está um exemplo:]

```
// Anexa os nomes das propriedades enumeráveis do objeto o no // array a e retorna a. Se a for omitido, cria e retorna um novo array. 

	function getPropertyNames(o, /* opcional */ a) { if (a === 
    undefined) a = []; // Se for undefined, usa um novo array 
    for(var property in o) a.push(property); return a; }

// Esta função pode ser chamada com 1 ou 2 argumentos:

	var a = getPropertyNames(o); // Obtém as propriedades de o em 
    um novo array getPropertyNames(p,a); 
    // anexa as propriedades de p nesse array
```
### Listas de argumentos de comprimento variável:
#### o objeto Arguments

Quando uma função é chamada com mais valores de argumentos do que os nomes de parâmetros existentes , não há maneira de se referir diretamente ao valores não nomeados.

O objeto ``Arguments`` oferece uma solução para esse problema . Dentro do corpo de uma função , o identifcadores ``arguments`` se refere ao objeto ``Arguments`` para essa chamada.

Esse objeto é semelhante a um array que permite aos valores de argumentos passados para a função serem recuperados por número , em vez de por nome.

O objeto arguments pode ser util de varias maneiras  . Um exemplo a seguir  mostra como é possivel utiliza-lo para verificar se uma função.

```
	function f(x,y,z) {
		if(arguments.length !=) {
			throw new Error("Function f called with " + arguments.length + "arguments , but it expected 3 arguments");
		}
		executa a função real...
	}

```

Note que muitas vezes é desnecessario verificar o numero de argumentos assim. O comportamento padrão de JavaScript é satisfatorio na maioria dos casos: os argumentos ausentes são ``undefined`` e os argumentos extras são simplesmente ignorados.

<hr>
Um uso importante  do objeto _ARGUMENTS_ é na escrita de funções que operam sobre qualquer número de argumentos.

A função a seguir aceita qualquer número de argumentos númericos e retorna o valor do maior argumento passado .

```
	function max(x) {
		var max = Number.NEGATIVE_INFINITY;
		// Itera os argumentos , procurando pelo maior numero
		for(var i = 0; i > arguments.length; i++) {
			if(arguments[i] > max) max = arguments[i]
		}
		return max;
	}
	var largest = max(1,10,100,2,3,1000,4,5,10000,6); // => 10000
```

Funções que podem aceitar qualquer número de argumentos são chamadas de _funções varíadicas , funções de aridade varíavel ou funções varags ._

<hr>
O objeto ``Arguments``  tem uma caracteristica _muito_ incomum. No modo não restrito , quando uma função tem paramêtros nomeados , os elementos do array do objeto Arguments são pseudônimos  dos parâmetros que contêm os argumentos da função . Os elementos numerados do objeto Arguments e os nomes de parâmetro são como dois nomes diferentes para a mesma variável . Mudar o valor de um argumento com nome muda o valor recuperado por meio do array arguments[x] , Vamos esclarecer isso :

```
	function f(x) {
		console.log(x); // Exibe o valor inicial do arg
		arguments[0] = null; //Muda o valor para null
		console.log(x); // Agora exibe ``null``
	}
```

<hr>
<h2> As proprieades callee e caller </h2>
O objeto `Arguments` define as proprieades ``callee`` e `caller` .

>[!WARNING]
>NO MODO RESTRITO DE ECMAScript 5 , É GARANTIDO QUE ESSAS PROPRIEADES LANCEM UM ``TyperError()`` SE VOCÊ TENTAR LÊ-LAS OU GRAVÁ-LAS.

A proprieade ``callee`` se refere a função que está sendo executada no momento .

``caller`` é uma proprieade não padronizadas , mas comumente implementada , que se refere a função que chamou aquela .
Ela da acesso a pilha de chamada e ocasionalmente a proprieade ``callee`` é util para permitir que funções não nomeadas chamem a si mesma recursivamente;

###### Exemplo:

	function check(args){
		var actual = args.length; // O numero real de parametros
		
		var expected = args.callee.length; // O numero de argumentos esperados
		
		if(actual !== expected) throw Error("Expected " + expected + "args; got " + actual)
	}
	function f(x,y,z) {
		check(arguments);
		return x+y+z;
	}
---

<h1>Closures</h1>
_Closures_ é a combinação de uma função e um escopo(um conjunto de vínculos de variável ) no qual as variáveis da função são solucionadas , é chamado de __Closures__

O primeiro passo para entender as _closures_ é examinar as regras do escopo léxico para funções aninhadas.

```
	var scope = "escopo global";

	function checkscope() {
		var scope = "escopo local";
		function f() {return scope;}
		return f();
	}
	checkscope(); // => "escopo local";
```

Vamos entender antes de passar um exemplo , sobre Escopo Léxico.

<h2> Escopo Léxico </h2>
>[!INFO]
>Ao declarar uma variável , o interpretador JavaScript determina se ela já existe no escopo atual . Dependendo de como essa variável foi declarada podemos ter certas atitudes em nosso codigo

A partir disso afirmamos que qualquer variável que criamos no escopo atual pertecencera aquele escopo

Escopos de variaveis globais podem ser visto em qualquer parte do codigo incluindo funções , métodos e outras chamadas de funções..

Mas e no caso de escopo aninhados ? A máquina irá procurar pela variável naquele escopo e se não acha-la , irá procurar no escopo externo mais próximo e assim por diante , até chegar a variável ou até chegar no escopo mais externo , ou escopo global 

Exemplo :

```
	var escopo = "global"; // variavel de escopo global visto em todo o codigo

	function() {
		var escopo = "local"; // variavel de escopo local visto somente nessa função. e nunca fora dela
	}
```

Ok .. Vamos enteder de fato oque são _CLOSURES_

Closures é quando uma função "lembra" seu escopo léxico , mesmo quando a função é executada fora deste escopo léxico.

---
## Construtora Function()

As funções normalmente são definidas pela palavra-chave ``function`` ou na forma de uma expressão de função literal . Mas as funções tambem podem ser definidas com a construtora ``Function`` Por exemplo:


````
	var f = new Function("x", "y", "return x + y");

	// Essa linha acima é a mesma coisa que a linha de baixo

	var f = function (x,y) {return x y}
	
````

Observe que a construtora ``Function()`` não recebe argumento algum especificando um nome para  a função que cria . Assim como funções literais , a construtora ``Function()`` cria funções anônimas 

-> Pontos importantes para entender a respeito da construtora Function();

- Ela permite que funções Javascript sejam criadas dinamicamente e copiladas em tempo de execução .
- Ela analisa o corpo da função e cria um novo objeto função cada vez que é chamada . Se a chamada da construtora aparece dentro de um laço ou de uma função chamada frequentemente , esse proceso pode ser ineficiente . Em contraste , as funções aninhadas e as expressões de definição de função que aparecem dentro de laços não são recompiladas cada vez que são encontradas.
- Um ultimo ponto importante sobre a construtora Function() __é que as funções que ela cria não usam escopo léxico__; em vez disso , são sempre compiladas como se fossem funções de nivel superior 
---
<h2> Objetos que podem ser chamados</h2>
Um _objeto que pode ser chamado_ é qualquer objeto que possa ser chamado em uma expressão de invocação de função. 

__Toda as funções podem ser chamadas , mas nem todos os objetos podem ser chamados de funções__

(Obs : o método ``toString()`` retorna uma string representando o objeto
Todo objeto possui um método `toString()` que é chamado automaticamente quando o objeto precisa ser representado como um valor em texto ou quando o objeto é referenciado de uma maneira que requeira uma string. Por padrão, o método `toString()` é herdado de todo objeto descendente de  `Object`. Se e o método não é sobrescrito em um objeto personalizado, `toString()` retorna "object _type_", onde `_type_` é o tipo do objeto. O código a seguir ilustra isso:)

---
<h1>High Order Functions</h1>
Uma _função de alta ordem_ é uma função que opera sobre funções , **recebendo uma ou mais funções como argumentos** e retornando uma nova função.

Exemplo:

```
	// Esta função de alta ordem retorna uma nova função que passa 
	// seus argumentos para f e retorna a negação lógica do vlor f

	function not(f) { // retorna uma função
		var result = f.apply(this, arguments);//que chama f
		return !results; // e nega seu resultado.
	}
```


Aqui está outro exemplo , mais geral , que recebe duas funções f e g e retorna uma nova função que calcula f(g());

```
	// Retorna uma nova função que calcula f(g(...)).
	// A função retornada h passa todos os args para g , então 
    //passa o valor de retorno de g para f e , em seguida , 
	//retorna o valor de retorno f.
	//Tanto f como g são chamadas com o mesmo valor de this com 
    //que h foi chamada.

	function compose(f,g) {
		return function() {
	// usamos a chamada de f porque estamos pasando um   
    //único valor e aplicamos em g porque estamos passando um 
    //array de valores.

		return f.call(this , g.apply(this, arguments ));
		}
	}

	var square = function(X){return x*x};
	var sum = function(x,y){ return x + y}
	var squareofsum = compose(square,sum)
```
---
<h1> Classes e modúlos</h1>
Os membros ou instâncias da classe têm suas proprieades próprias para conter ou definir seu estado.

Em JavaScript , as classes se baseiam no mecanismo de heranças baseados em protótipos da linguagem.

__Se dois objetos herdam proprieades do mesmo objeto protótipo , dizemos que eles são instâncias da mesma classe__

Uma das caracteristicas importantes de classes em Javascript é que elas podem ser extendidas dinamicamente.

As classes podem ser consideradas como tipos;
<h2> Classes e protótipos </h2>
Em Javascript , uma classe é um conjunto de objetos que herdam proprieades do mesmo objeto protótipo. Portanto , o objeto protótipo é o principal recurso de uma classe. 

<h2> Classes e construtoras </h2>
>[!IMPORTANT]
>Uma construtora é uma função destinada á inicialização de objetos recém-criados

As construtoras são chamadas usando-se a palavra-chave ``new`` . As chamadas de construtoras que utilizam `new` criam um novo objeto automaticamente , de modo que a construtora em si só precisa inicializar o estado desse novo objeto .

A caracteristica fundamental das chamadas de construtoras é que a propriedade prototype da construtora é usada como protótipo do novo objeto .

Isso significa que todos os objetos criados com a mesma construtora herdam do mesmo objeto e , portanto são membros da mesma classe.

## Construtoras e identidade de classes

Dois objetos são instancias da mesma classe se , e somente se , herdam do mesmo objeto protótipo . 

Duas funções construtoras podem ter proprieades `prototype` que apontam para o mesmo objeto protótipo . Então as duas construtoras podem ser usadas para criar instâncias da mesma classe.

As construtoras atuam como identidade pública das classes , mas os protótipos são a identidade fundamental.

## Classe estilo Java em Javascript

Um modo pelo qual Javascript se diferencia da linguagem Java é que suas funções são valores e não há distinção rígida entre métodos e campos.

Se o valor de uma propriedade é uma função , essa prop então define um método ; caso contrário , é apenas uma propriedade ou ''campo'' normal.

Em JavaScript existem três objetos diferentes envolvidos em qualquer definição de classe e as propriedades desses três objetos atuam como diferentes tipos de membros de classe  :

_Objeto construtor_
	Conforme observamos , a função construtora (um objeto) define um nome para uma classe Javascript. As proprieades adicionadas nesse objeto construtor servem como campos de classe e métodos de classe (dependendo de os valores de proprieades serem funções ou não).

_Objeto protótipo_
	As propriedades desse objeto são herdadas por todas as instâncias da classe e as proprieades cujo valores são funções se comportam como métodos de instâncias da classe.

_Objeto instância_
	Cada instância de uma classe é um objeto por si só e as proprieades definidas diretamente em uma instância não são compartilhadas por qualquer outra instância . As proprieades que não são função , definidas em instâncias , se comportam como os campos de instâncias da classe.

##### Duck Typing ou Tipagem do pato
>[!ANSWER]
>Uma filosofia da programação que se concentra no que um objeto pode fazer (quais métodos ele tem) e não a qual é a sua classe.

>[!QUOTE]  
>  Quando vejo um pássaro que caminha com um pato , nada como um pato e grasna como um pato , chamo esse pássaro de pato

Para programadores Javascript , essa definição pode ser entendida como 'se um objeto caminha nada e grasna como um Pato então podemos tratá-lo como um Pato, mesmo que não herde do objeto protótipo da classe Pato

---
## Expressões regulares

##### Flags
 Os flags de expressões regualares especificam regras de comparação de padrões de alto nível 
 ![[Pasted image 20220711132226.png]]
 ---
<h1>    JavaScript do lado client </h1>





















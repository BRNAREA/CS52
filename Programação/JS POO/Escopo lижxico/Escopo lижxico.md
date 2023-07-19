#      Escopo léxico em JavaScript

Antes de entendermos o que é um _Escopo léxico_ precisamos saber se JavaScript é uma linguagem _compilada_ ou _interpretada_.

(Você pode ler um pouco sobre compilação em ([[Compiladores Principios Tecnicas e Ferramenta - by Alfred V.]]))

Fazendo um resumão do que seria uma compilação : é um processo onde o código fonte é analisado , e possivelmente transformado em código alvo. Ou seja , a sua execução ocorre posteriormente.

Ja na interpretação , é necessario um interpretador e a análise do código fonte ocorre junto ao seu uso. Essa análise é feita todas as vezes que o código for executado , oque faz com que os erros sejam encontrados apenas durante a execução.

Isso significa que aplicações interpretadas executam o código fonte analisado , enquanto aplicações compiladas geram um outro código para ser usado posteriormente po um ambiente que consiga entendê-lo ( uma VM , por exemplo).

Então , JavaScript seria uma linguagem Interpretada.

Mas , Por que ? Na maioria dos casos , os navegadores hoje em dia compilam o código fonte em código nativo ( oque pode gerar a confusão) , porém o código fonte em código nativo ( o que pode gerar a confusão), porém a análise deste código fonte é feita todas as vezes antes da execução , fazendo com que os erros sejam encontrados ao executar. Isso caracteriza a linguagem como interpretada.

Dito isso , logo antes da execução do código ocorre um processo chamado _lexing_ , ou tokenização , onde uma sequência de caracteres é transformada em uma sequência de tokens . Nesse momento , o escopo é definido , ou seja , o escopo léxico é definido pela pessoa desenvolvedora durante a criação do código e preservado pelo _lexer_.

Ao declarar uma variável , o interpretador determina se ela já existe dentro do escopo atual . Dependendo da forma como essa variável é declarada , podemos ter alguns comportamentos distintos , que veremos em mais detalhes em hoisting e as formas de se declarara variáveis.

Mas e no caso de escopos aninhados ? A máquina irá procurar pela variável naquele escopo e se não achá-la , irá procurar no escopo externo mais próximo e assim por diantes, até achar a variável ou até chegar o escopo mais externo , ou escopo global. Todos os script tem acesso a este escopo.

O escopo está aninhado dentro do escopo global , logo , tudo o que está definido dentro de foo está escondido para o mundo externo isso também é chamado de _variable shadowing_

```javascript
	var nome = "Maria";
	function foo() {
		var nome = "Joao";
		console.log(nome);
	}
	console.log(nome); // Maria
	foo(); //João
```

Apalavra reservada ``let`` pode ser utilizada no lugar de ``var`` , ela , inclusive , "prende" a declaração da varíavel ao escopo do bloco em que ela está contida.

É muito útil em declarações de loops `for` pois evita que variáveis de mesmo nome (e escopo diferentes) colidam , assim como evita poluição de escopo , alé, de fazer o _binding_ a cada iteração do loop , oque é útil também para closures.



















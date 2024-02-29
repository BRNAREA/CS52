#                         fetch

A função ``fetch()`` retorna uma _Promisse_ ([[Promises]]) 

<h2>Usando Fetch</h2>
A <u><b>API Fetch</b></u> fornece uma interface JavaScript para acessar e manipular partes do pipeline HTTP, tais como os pedidos e respostas . Ela também  fornece o método global `fetch()` que fornece uma maneira fácil e lógica para buscar recursos de forma assíncrona através da rede.


Este tipo de funcionalidade era obtidade anteriormente utilizando `XMLHttpRequest` . Fetch fornece uma alternativa melhor que pode ser facilmente utilizada por outras tecnologias como `Service Workers` . Fetch também provê um lugar lógico único para definir outros conceitos relacionados ao protocolo __HTTP__ como _CORS_ e extensões ao HTTP.

>[! QUESTION]
>Oque é um protoclo HTTP ?
>Leia em -> [[Explicando o HTTP]]

- A Promise retornada do `fetch()` __não rejeitará o status do erro HTTP__ mesmo que a resposta seja um HTTP 404 ou 500. Em vez disso , ela irá resolver normalmente (com o status `ok` definido como falso) , e só irá rejeitar se houver falha na rede ou se impedir a requisição de ser completada.
- `fetch()` __não receberá cookies cross-site;__ você não pode estabelecer uma conexão cross-site usando fetch. Cabeçaçhos `Set-Cookie` de outro sites são ignorados silenciosamente.
- `fetch()` __não enviará cookies__ , nçao ser que seja definida a opção _credentials_ do <u>parâmetro init</u> (Desde 25 de agosto de 2017). A especificação alterou as políticas padrão de credenciais para `same-origin` . O Firefox mudou desde 61.0b13.)


<h2> Fazendo as requisições Fetch </h2>
 Uma requisição fetch é realizada para configuração . Temos um exemplo no seguinte código:

```javascript
	var myImage = document.querySelector('img');

	fetch('flowers.jpg')
		.then(function(response) {
			return response.blob();
		})
		.then(function(myBlob)){
			var objectURL = URL.createObjectURL(myBlob);
			myImage.src = objectURL;	
		 }
```

Aqui estamos procurando uma imagem e inserindo em um elemento `<img>`. O uso mais básico do `fetch()` acarreta em um argumento - a pasta do recurso que você deseja buscar - e retorna uma promessa contendo a resposta (a `Response` object).

Esta é apenas uma respota __HTTP__ , não a imagem em sí. Para extrairmos a imagem da resposta , nós usamos o método `blob()` (definido no mixin do `Body`, que são implementados por ambos do objetos `Request` e `Response`).


<h3> Fornecendo opções de request </h3>
O método `fetch()` pode receber um segundo parametro opcional , que consistem em um objeto `init` que permite várias configurações:

```javascript
var myHeaders = new Headers();

var myInit = { method: 'GET',
			  headers: myHeaders,
			  mode: 'cors',
			  cache: 'default'

};

fetch('flowers.jpg', myInit)
	.then(function(response){
		return response.blob();
	})
	.then(function(myBlob){
		var objectURL = URL.createObjectURL(myBlob);
		myImage.src = objectURL;
	});
```

![[Pasted image 20220711225510.png]]
#### Verificando se o fetch foi bem sucedido

Uma promise `fetch()` será rejeitada com um TypeError quando um erro de rede é encontrado , embora isso geralmente signifique problemas de permissão ou similar — um 404 não constitui um erro de rede , por exemplo. Uma verificação precisa de um `fetch()` bem-sucedido incluiria a verificação de que a promessa foi resolvida e , em seguida , a verificação de que a propriedade <u>Responde.ok</u> tem o valor de `true` .

```javascript
fetch('flowers.jpg').then(function(res) {
	if(response.ok) {
		response.blob().then(function(myBlob){
			var objectURL = URL.createObjectURL(myBlob);
			myImage.src = objectURL;
		});
	} else {
		console.log('Network response was not ok.');
	}
})
.catch(function(error) {
	console.log('Aconteceu algum problema com a operação Fetch' + error.message);
})
```

<h3> Fornecendo seu próprio objeto de solicitação</h3>
Em vez de passar um caminho , para o recurso que você deseja solicitar , dentro da requisição `fetch()` , você pode criar um objeto de solicitação usando o construtor `Request()` , e então passar a solicitação como um argumento do método `fetch()` :

```javascript
	var myHeader = new Headers();
	var myInit = {method: 'GET',
			      headers: myHeaders,
			      mode: 'cors',
			      cache: 'default'};	

var myRequest = new Request('flowers.jpg', myInit);

fetch(myRequest)
	.then(function(response) {
		return response.blob();
	})
	.then(function(myBlob) {
		var objectUR = URL.createObjectURL(myBlob);
		myImage.src = objectURL;
	})
```

``Request()`` aceita exatamente os mesmos parâmetros do método `fetch()` . Você pode ser até mesmo passar um objeto de solicitação de solicitação existente para criar uma cópia dele:

```javascript
var anotherRequest = new Request(myRequest, myInit);
```

Isso é muito útil , pois conteúdos de cada solicitação e respostas tem apenas um uso . Fazer uma cópia como essa permite que você use a solicitação / respostas novamente , variando as opções de inicialização , se desejar.

###                                  Headers
A interface permite que você crie seus proprios objetos headers por meio do construtor `Headers()` . Um objeto headers é um mapa multidimensional simples de nomes para o valor?

```javascript
var content = "Hello World";
var myHeaders = new Headers();

myHeaders.append("Content-Type", "text/plain");
myHeaders.append("Content-Length", content.length.toString());
myHeaders.append("X-Custom-Headers", "ProcessThisImmediately");
```

O mesmo pode ser feito passando um array de arrays ou um objeto literal para contrutor:

```javascript
myHeaders = new Headers({
	"Content-Type": "text/plain",
	"Content-Length": content.length.toString(),
	"X-Custom-Header": "ProcessThisImmediately",
})
```

O conteúdo pode ser consultado e recuperado:

````
```
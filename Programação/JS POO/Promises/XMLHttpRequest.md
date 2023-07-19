<h1> Fazendo XMLHttpRequest cumprir promessas</h1>
APIs antiga serão atualizadas para usar promessas , se for possível de uma maneira compatível com versões anteriores. O objeto ``XMLHttpRequest`` é um candidato importante , mas por enquanto vamos escrever uma função simples para fazer uma solicitação GET:

```javascript

	function get(url) {
		// Retorne uma nova promessa.
		return new Promise(function(resolve, reject) {
			// Faça o trabalho usual do XHR

		var req = new XMLHtttRequest();
		req.open('GET', url);

		req.onload = function() {
			// Chamado em caso de 404 etc
			// Então verifique o status
		if(req.status === 200) {
			//Resolva a promessa com o texto em response 
			resolve(req.response);
		}
		else {
			// Caso contrário rejeite com o texto do status
			// que esperamos que seja um erro que possamos enteder
			reject(Error(req.statusText));
		}
		
		// Lide com erros de rede
		req.onerror = function() {
			reject(Error("Newtowrk Failure"));
		};

		// Faça a requisição
		req.send();
		})
	}
```
![[Pasted image 20220708235357.png]]

Agora vamos usá-la:
```javascript
	get('story.json').then(function(response) {
		console.log("Sucess", response);
	})
```

## Encadeamento
O ``then()`` não é o fim da história. Você pode encadear vários ``then`` um no outro para transformar valores ou executar ações assíncronas adicionais uma depois da outra.

###### Transformando valores
Você pode transformar valores simplesmente retornando o novo valor: 

```javascript

	var promise = new Promise(function(res,rej {
		resolve(1);
	}))

	promise.then(function(val) {
		console.log(val); // 1
		return val + 2;
	}).then(function(val) {
		console.log(val);//3
	})
```

A resposta ( response ) é JSON , mas ela está aqui sendo recebida como texto simples.

Poderíamos alterar nossa função get para usar o <u>respondeType</u> JSON , mas também podemos deixar para resolver isto na terra das promessas:

```javascript
	get('story.json').then(function(response) {
		return JSON.parse(response);
	}).then(function(response) {console.log("YEY JSON", response)})
```

Na verdade , poderíamos criar uma função ``getJSON()`` de forma relativamente simples:

```javascript
	function getJSON(url) {
		return get(url).then(JSON.parse);
	}
```

A função ``getJSON()`` ainda retorna uma promessa. Uma promessa que busca uma url e depois processa a resposta como JSON.

###### Enfileirando ações assíncronas

Você também pode encadear vários ``then`` para executar ações assíncronas em sequência.

Quando você retorna alguma coisa de um callback `then` , é meio mágico. Se você retornar um valor , o próximo `then` será chamado com esse valor. No entanto , se você retornar algo que pareça uma promessa , próximo `then()` espera por ele e só é chamado quando a promessa for cumprida (sucesso/falha). Por exemplo

```javascript
	getJSON('story.json').then(function(`story`) {
		return getJSON(sotry.chapterUrls[0]);
	}).then(function(chapter1) {
		console.log("Got chapter 1", chapter1);
	})
```
Aqui , fazemos uma solicitação assíncrona para `story.json` , que nos dá um conjunto de URLs a serem solicitadas e , em seguida , solicitamos a primeira delas. É nesse ponto em que promessas realmente começam a ganhar destaque em relação ao uso clássico de [[callbacks]]. 

Você pode até criar um método de atalho para obter os capítulos:

```javascript
	var storyPromise;

	function getChapter(i) {
		storyPromise = storyPromise || getJSON('story.json');

	return storyPromise.then(function(story) {
		return getJSON(story.chapterUrls[i]);
	})

	// é facil de usar:
	getChapter(0).then(function(chapter) {
		console.log(chapter);
		
		return getChapter(1);
	}).then(function(chapter) {console.log(chapter);})
	}
```

Nós não baixamos o `story.json` até que `getChapter` seja chamado , mas da próxima vez que `getChapter` for chamado , reutilizamos a promessa de história, portanto , `story.json` é baixado apenas uma vez. Viva as promessas !
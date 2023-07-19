##### .catch nas Promises

Esse método serve como uma "captura" de erro em caso da Promise não for bem sucedida . Usamos .catch em caso de retorno [[rejected]].

Não há nada de especial em usar `catch()` , é apenas uma alternativa equivalente a `then(undefined, func)`, mas é mais legível . Observe que os dois exemplos de código acima não se comportam da mesma forma , o último é equivalente a:

```javascript

	get('story.json').then(function(res) {
		console.log("Success", res);
	}).then(undefined, function(err) {console.log("Fail", err)})
```

A diferença é sutil , mas extremamente útil . As rejeições da promessa passam para o próximo `then()` com um "callback de rejeição" (ou `catch()` , já que é equivalente).

Com `then(func1, func2)` , será chamada ou a função `func1` ou `func2` , mas nunca as duas . Mas com `then(func1).catch(func2)` , ambas serão chamadas se `func1` rejeitar , pois são etapas separadas na cadeia . Exemplos:

```javascript
	asyncThing1().then(function(){
		return asyncThing2();
	}).then(function() {
		return asyncThing3();
	}).catch(function(err){
		return asyncRecovery1();
	}).then(function() {
		return asyngThing4();
	}).catch(function(err) {
		return asyncRecovery2();
	}).
```

O fluxo acima é muito parecido com o try/catch típico do JavaScript, os erros que acontecem em um "try" vão imediatamente para o bloco `catch()`.
Exemplo com fluxograma:
![[Pasted image 20220709011346.png]]
->Siga as linhas __azuis__ para as promessas que se cumprem , ou as vermelhas para as que são rejeitadas.

As rejeições acontecem quando uma promessa é rejeitada explicitamente , mas também implicitamente se um erro for lançado no callback do construtor.
Ex:

```javascript
	var jsonPromise = new Promise(function(resolve, reject) {
		//JSON.parse provoca um erro se você alimentá-lo com 
		//JSON inválido , então isto implicitamente causa rejeição

		resolve(JSON.parse("ISTO NÃO É JSON"));
	});

	jsonPromise.then(function(data) {
		// Isto nunca acontece:
		console.log("Funcionou!", data);
		
	}).catch(function(err) {
		// isto acontece ! :
		console.log("Falha", err);
	})
```

Com nossa história e capítulos , podemos usar catch para exibir um erro ao usuário:

```javascript
	getJSON('story.json').then(function(story) {
		return getJSON(story.chapterUrls[0]);
	}).then(function(chapter1) {
		addHtmlToPage(chapter1.html);
	}).catch(function() {
		addTextToPage("Falha ao mostrar o capítulo");
	}).then(function() {
		document.querySelector('.spinner').style.display = 'none';
	})
```

Se a busca de `story.chapterUrls[0]` falhar ( por exemplo, http 500 ou se o usuário estiver offline) , __TODOS__ os callbacks de sucesso seguintes serão ignorados . Isto inclui aquele que está no `getJSON()` que tenta processaro a resposta como JSON.  Também será ignorado o callback que adiciona capitulo1.html à pagina. Em vez disso será executado o callback do catch. Como resultado , "Falhas ao mostrar o capitulo" será adicionado à página se qualquer uma das ações anteriores falhar.

Assim como o try/catch do Javascript o erro é detectado e o código subsequente continua, então o spinner estará sempre oculto , que é o quer queremos . O código acima se torna uma versão assíncrona sem bloqueio de :

```javascript
	try {
		var story = getJSONSync('story.json');

		var chapter1 = getJSONSync(story.chapterUrls[0]);
		addHtmlToPage(chapter1.html);
	}
	catch (e) {
		addTextToPage("Falha ao mostrar o capítulo");
	}
	document.querySelector('.spinner').style.display = 'none'
```
Talvez você queira executar o `catch()` simplesmente para fins de registro , sem se recuperar do erro.  Para isto , basta relançar o erro. Podemos fazer isto no nosso método `getJSON()`:

```javascript
	function getJSON(url){
		return get(url).then(JSON.parse).catch(function(err) {
			console.log("getJSON failed for" , url,err);
			throw err;
		})
	}
```
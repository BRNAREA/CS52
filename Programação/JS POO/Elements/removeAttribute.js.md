# removeAttribute.js

## como remover um atributo com o metodo removeAttr ?

Bom agora que você já sabe como criar um atributo está na hora de saber como remove-lo , afinal você não quer os atributos fiquem para sempre no elemento não é ? Então vamos lá.

Se você criou um atributo para um elemento em especifico então será mais facil remove-lo basta você adicionar o método  `.removeAttribute("style")` com o parametro do atributo que deseja remover.. Simples não é ?

Agora vamos para o caso numero 2.. 

Caso você tenha um vetor , ou seja um array de elementos resgatados a partir de algum metodo . você precisará percorrer esse vetor para que não você não tenha que colocar um por um então vamos: 

	// Primeiro resgatamos as Tags
	var tags = document.getElementByTagName("p"); // Pegamos todos os elementos com a tag "p"
	
	Agora temos que fazer o loop para percorrer todas essas tags que estão na variavel tags : vamos la ..
	
	for (var i = 0;i<tags.lenght; i++) {
		tags[i].removeAttribute("style");
	}
	

Poderiamos tambem usar o metodo [[toggleAttribute().js]] , com ele as tags que teriam o atributo seriam removidas e as que não teriam , agora estariam com a tag . Dê uma olhada na seção.
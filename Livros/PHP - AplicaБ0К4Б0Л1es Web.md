
***¹Funcionamento do protocolo http***

Quando digitamos um endereço (URL) no navegador ou clicamos num link , o navegador fará uma requisição ao servidor http do tipo GET. (ver capitulo 02).

Essa requisição terá uma algumas linhas de cabeçalhos (headers) , e receberá como resposta um arquivo , tabém com linhas de cabeçalho , que geralmente é uma pagina no formato **HTML** . Se essa página contiver uma ou mais imagbens (tag <img..>), será feita mais uma requisição para cada imagem.

>[!IMPORTANT]
>
A maneira que o navegador tem de identifcar se á requisição é uma pagina html , um arquivo txt , uma imagem , documento pdf ou qualquer outro formato é atraves de um header de respostas chamado de  ``“Content-type”.`` Através do conteúdo desta linha é possivel identificar o tipo de arquivo.


Assim que o arquivo de respota é enviado a conexão é encerrado. Fazendo com que cada nova página gere uma nova requisição completamente independente da anterior , o que impede de haver uma identificação por parte do servidor da origem da requisição .
<u>Sem artifícios seria impossível fazer uma loja virtual , por exemplo, pois no momento de pagar a compra o servidor não saberia quais os itens já selecionados , por não haver ligação entre a requisição feita para selecionar o item e a requisição feita para pagar a compra.</u>

O Principal artíficio usado para isso é o *cookie* , (Veja aqui oque é um cookie na seção -> [[cookies]]) , que tem a <u><b>Função de enviar uma identificação junto com cada requisição , tornando possível a associação entre as requisições.**</b></u>

(Você pode ler um pouco mais sobre protocolo HTTP em : [[Explicando o HTTP]] )

---


>[!WARNING]
>[!IMPORTANT]
>Um outro poblema do protocolo http é que o servidor só pode enviar informações quando há uma solicitação . Ele nunca enviar automaticamente informações para o navegador , e por isso não pode validar dados digitados sem que os mesmo sejam enviados com uma requisição.

>[!ANSWER]
>A solução para o problema acima é utilizar client-side scripts.

---

***²Client-Side Scripts***
	Os scripts client-side são muito úteis para fazer validações de formulários sem utilizar processamento do servidor e sem provocar tráfego na rede. Outra utilização comum é na construção de interfaces dinâmicas e “leves”.

*Exemplos de script client-side* :
<iframe 
		width=960
		height=267
		src="https://www.widerfunnel.com/wp-content/uploads/2017/04/Basic-Static-App-Server.png"></iframe>
---
***³Server-Side Scripts***
Os scripts server-side são resposáveis pela criação de páginas em tempo real . Num mecanismo de busca , por exemplo , seria invíavel manter um arquivo para cada consulta a ser realizada. O que existe é um modelo da página de resposta , que é mesclado com os dados no momento em que a página é requisitada.
			O cliente (navegador) não é capaz de diferenciar páginas estáticas de páginas dinâmicas , a não ser que o script gerador da página dinâmica envie alguma informação desse tipo.

<iframe 
		width=960
		height=227
		src="https://i.ytimg.com/vi/nhZMH8oX6xI/maxresdefault.jpg"></iframe>
## Oque pode ser feito com PHP?

	Basicamente , qualquer coisa pode ser feita por algum programa CGI pode ser feita também com PHP, como coletar dados de um formulario , gerar páginas dinamicamente ou enviar e receber cookies.

	PHP támbem tem uma das características mais importantes o suporte a um grande número de banco de dados , como dBase, Interbase, MS-SQL Server, mySQL, Oracle , Sybase , PostgreSQL e vários outros.

	Além disso , PHP tem suporte a outros serviços através de protocolos como IMAP , SNMP , NNTP ,POP3 e , logicamente , o HTTP. Ainda é possivel abrir sockets e interagir com outros protocolos
---

## Nascimento da linguagem
- Criada em 1994
- por Rasmus Lerdof
- utlizada antigamente somente para home-page apenas para que ele pudesse ter informações sobre visitas que estavam sendo feitas.
- Primeira versão disponibilizada em '95.

- Ficou conhecida como “Personal Home Page Tools” , posteriormente na v.3 o PHP foi reescrito por **Zeev Suraski** e **Andi Gutmans** quando deixou de ter o nome antigo e passou para o nome Hypertext Preprocessor.

---
## Enviando Dados para o servidor HTTP

	Programar para web pode ser considerado como um jogo que consiste em receber os dados do usuário , processá-los e enviar a respota dinâmica . Uma vez enviada a resposta , é encerrado contato entre o servidor e o cliente . Portanto a primeira coisa a aprender é como fazer para receber os dados enviados pelo browser para o servidor.

	O protocolo HTTP provê dois principais métodos para enviar informações para o servidor web , além da URL referente ao arquivo solicitado . Esses métodos são o POST e o GET.

	O protocolo HTTP/1.0 também especifica o método HEAD, utilizado apenas para transmitir informações do header , além dos métodos PUT e DELETE , que não serão abordados por aqui.

### O método GET

A especificação do protocolo HTTP/0.9 (a primeira implementação do HTTP) possuía a definição do método *GET* , utlizados pelo browser para <b><u>solicitar um documento específico</b></u>.

Por exemplo : a seguinte requisição HTTP retornaria o documento "index.html" m localizado no diretório do servidor chamado "teste";

	``GET /teste/index.html CRLF``

Devemos notar que a requisição *GET* inicia com a palavra *GET* , inclui o documento solicitado e encerra a combinação dos caracteres *carriage return* e *line feed*.
	Para um melhor entendimento , você pode fazer uma requisição GET conectando diretamente em algum servidor **WEB** , conectando através de um programa de telnet (geralmente o servidor http utiliza a porta 80). A resposta será o código da página solicitada.

````
	telnet www.guia-aju.com.br 80
	Trying 200.241.59.16...
	Connected to www.guia.aju.com.br.
	Escape characteres is '^'.
	GET /index.php3
	(...página solicitada...)
	connection closed by foreign host.
````

Através do método  *GET* também é possível **passar parâmetros da requisição do servidor** , que pode tratar esses valores e até alterar a resposta a depender deles , como no exemplo abaixo :

````
	telnet www.guia-aju.com.br 80
	Trying 200.241.59.16...
	Connected to www.guia.aju.com.br.
	Escape character is '^'.
	GET /index.php3?id=0024horas&tipo=Taxi
	(...página solicitada ...)
	Connection closed by foreign host.
````

	No exemplo são passados dois parâmetros : id e tipo. Esses parâmetros estão no formato conhecido por URLencode.

Apesar de ser possível passar parâmetros utilizando o método *GET* , e com isso páginas dinamicamente , este método tem pelo menos dois problemas que em determinadas circunstâncias podem ser considerados sérios :

¹ O primeiro é que o *GET* permite uma quantidade de dados passados a 1024 caracteres , oque pode gerar perda de informações em certos casos.

² O segundo é que pelo fato de que as informações fazerem parte da URL , todos os dados podem ser visto pelo usuário . Isso pode ser extremamente perigoso quando informações sigilosas estão envolvidas (senhas , por exemplo).

---
## Headers

Os *headers* **são informações trocadas entre o navegador e o servidor** **de maneira transparente ao usuário** , e podem conter dados sobre o tupo e a versão do navegador , a página de onde partiu a requisição (link) , os tipos de arquivos aceitos como respostas , e uma série de outras informações.

Assim foi possível definir um outro método de requisição de arquivos , que resolveu os principais problemas do método *GET*.

---
### O método POST
 Através da utilização de headers é poissivel enviar parâmetros da URL solicitada sem expor esses dados ao usúario , e também sem haver um limite de tamanho. 

  Uma conexão ao servidor HTTP utilizando o método *POST* seria algo semelhantes ao que segue:
````
	telnet www.guia.aju.com.br 80
	Trying 200.241.59.16...
	Connected to www.guia-ajuda.com.br
	Escape character is '^'.
	POST /index.php3
	Accept */*
	Content-type: application/x-www-form-urlenconded
	Content-length:22

	id==0024horas&tipo=Taxi
	(... página solicitada ...) =
	Connection closed by foreign host.
````

A linha __“Accept”__ informa os tipos de dados que podem ser enviados como resposta (no caso , todos) .

A linha __“Content-Type”__ informa o tipo de dado que está sendo enviado (urlencoded).

O terceiro header é o mais importante pois informa o tamanho do corpo da mensagem ,que contém os parâmetros.

# Utilizando GET e POST
O método **GET** pode ser utilizado atráves de um endereço no local apropriado do navegador ou atráves de um hiperlink , ou seja , uma referência de uma pagina a outra. A terceira maneira de utilizar o **GET** é através de formulários ``HTML`` , e neste caso o usuário não precisa se preocupar com a codificação dos dados. A utilização de formulários ``HTML`` é a unica maneira possivel de submeter dados pelo método **POST**.

---
 # Definindo um formulário

Pelo fato dos formulários serem feitos em HTML então precisamos da seguintes tag : <form name=" " action=" " method=" " enctype=" "> </form>

	Onde temos
	name : o identificador do formulário . Utilizado principalmente em Scripts clien-side (JavaScript);

	action : nome do script que receberá os dados do formulário ao ser submetido. Mais à frente estão abordadas as maneiras de tratar os dados recebidos;

	method : método de envio dos dados : get ou post;
	enctype : formato em que os dados serão enviados . O default é urlencoded. Se for utilizado um elemento do tipo upload de arquivo (file) é preciso utilizar o tipo multipart/form-data.

Exemplo :
	<form action="exemplo.php" method="post">
		(textos e elementos do form)
	</form>

## Upload de arquivos 
<input type="file" name="" size="">

Exibe na tela do browser um campo de texto e um botão, que ao clicadoabre uma janela para localizar um arquivo no disco. Para utilizar este tipo decomponente, o formulário deverá utilizar o método “POST” e ter o parâmetro “enctype”com o valor "multipart/form-data".

---
## Listas

	As listas sao utlizadas em PHP para realizar atribuicoes multiplas . Atraves de listas e possivel atribuir valores que estao num array para variaveis . Exemplo :

```
	list($a, $b, $c) = array("a", "b","c");
```

---
# Oque e um "Objeto" em PHP ?
## Objetos

 Um ``Objeto`` pode ser inicializado utilizando o comando ``new`` para instanciar uma classe para uma variavel.

Exemplo: 
```
	class teste {
		function nada(){
			echo "nada";
		}
	}
	$vivas = new teste;
	$vivas -> nada();
```

---
#### Booleanos
A maneira de avaliar as expressoes e retornar ``true`` ou ``false`` e atraves do tipo ``integer`` : e usado o valor 0 (zero) ou vazio (String vazia) para representar o estado ``false`` e qualquer valor diferente de zero (geralmente 1) para representar o valor ``true``.

---
## Transformacao explicita de tipos

Os tipos de *cast* permitido sao : 

(int), (integer) => muda para integer;
(real), (double), (float) => muda para float;
(string) => muda para string;
(array) => muda para array;
(object) =>muda para objeto.

### Com a funcao settype
A funcao *S E T T Y P E* converte uma variavel para o tipo especificado que pode ser "integer", "double", "string" , "array" ou "object".

Exemplo:
```
	$vivas = 15; // $vivas e integer
	settype($vivas,double) // $vivas e double
```

---
## Controle de erro

>[!INFO]
>>PHP Suporta um operador para controlar erros: 
``@`` | Operador de controle de erros

Quando esse operador e utilizado antes de uma expressao , qualquer mensagem de erro que possa ser gerada pela expressao sera omitida.
Se a opcao *t r a c k _  e r r o r s* estiver halitada no arquivo php.ini , a mesangem sera armazenada na variavel ``$php_errormsg.`` 

---
#### foreach
Incluido na versao 4 do PHP , utilizado para percorrer os elementos de um array . Sua sintaxe e bem simples :

```
	foreach(array as $valor) expression
	foreach(array as $key => $value) expression
```
Sendo que a expressao pode conter um bloco de expressoes.

O uncionamento do comando *foreach* e bastante simples: no inicio da execucao o array e reiniciado , ou seja , o **ponteiro** do array passa a apontar para o primeiro elemento , dispensando o uso da funcao *r e s e t*
. A cada execucao o laco de um elemento do array e selecionado , atribuindo valor as variaveis $value e $key com valor e a chave do elemento selecionado , sendo que essas variaveis podem ser utilizadas dentro do laco.

Exemplo:
```
foreach($arr as $key => $value) {
	echo "chave : $key; Valor: $value <br>/n";
}
```

---
<h2> Funções </h2>
Em suma funções foram feitas para reutilzar o codigo em varias partes do programa reduzindo a mão de obra.
<h3> Valor de retorno </h3>
	Toda função pode opcionalmente retornar um valor , ou simplesmente  executar os comandos e não retornar valor algum.

Não é possivel que uma função retorne mais de um valor , mas é permitido fazer com que uma função retornar um valor composto , como listas ou arrays.

<h3>Argumentos </h3>
	É possivel passar argumentos para uma função . Eles devem ser declarados logo após o nome da função , entre parênteses , e tornam-se variáveis pertencentes ao escopo local da função . A declaração do tipo de cada arugumento também é utilizada apenas para efeito de documentação.

Exemplo : 
```
	function imprime($texto) {
		echo $texto;
	}
	imprime("teste de função");
```

**Passagem de parâmetros por referência**

 Normalmente  , a passagem  de parâmetros em PHP é feita por valor , ou seja , se o conteúdo da variável for alterado , essa alteração não afeta a variável original.

Exemplo:
```
	function mais5($numero) {
		$numero += 5;
	}
	$a = 3;
	mais5($a); // $a continua valendo 3
```

No exemplo acima, como a passagem de parâmetros é por valor, a função _mais5_ é inútil, já que após a execução sair da função o valor anterior da variável é recuperado. Se a passagem de valor fosse feita por referência, a variável $a teria 8 como valor. 

O que ocorre normalmente é que ao ser chamada uma função, o interpretador salva todo o escopo atual, ou seja, os conteúdos das variáveis. Se uma dessas variáveis for passada como parâmetro, seu conteúdo fica preservado, pois a função irá trabalhar na verdade com uma cópia da variável. 
Porém, se a passagem de parâmetros for feita por referência, toda alteração que a função realizar no valor passado como parâmetro afetará a variável que o contém.

Há duas maneiras de fazer com que uma função tenha parâmetrospassados por referência: indicando isso na declaração da função, o que faz com que apasagem de parâmetros sempre seja assim; e também na própria chamada da função.Nos dois casos utiliza-se o modificador “&”. Vejamos um exemplo que ilustra os dois caso :

```
	function mais5(&$num1, $num2) {
		$num1 += 5;
		$num2 += 5;
	}
	$a = $b = 1;
	mais5($a, $b)
```
Em PHP é possivel tambem ter valores "``default``" para argumentos de função , ou seja valores que serão assumidos em caso de nada ser passado no lugar do argumento Exemplo : 

```
	function teste($vivas = "testando"){
		echo $vivas; 
	}

	teste(); //Imprime "testando";
	teste("outro teste"); //Imprime "outro teste"
```
>[!WARNING]
>É bom lembrar que quando a função tem mais de um parâmetro , oque tem o valor ``default`` deve ser declarado por ultimo :
```
	function teste() {
		echo "a figura é um", $figura, "de cor " $cor;
	}

teste(azul);
```

---
<h2>Funções variáveis</h2>
PHP suporta o conceito de funções variáveis . Isso significa que **se uma variável** tiver __parênteses__ ao final , a __função__ cujo __nome__ for o __valor__ da variável será executada , se existir.

```
	function soma($a, $b){
		return $a + $b;
	}

	function multiplica($a, %b) {
		return $a * $b
	}

	function dobro($a) {
		return 2 * $a;
	}

	$func = 'soma';
	echo $func(4,5)
	$func = 'multiplica'
	echo $func(4,5);
	$func = 'dobro'
	echo $func(4);
```

---
<h2> O modificador static </h2>
Uma variável estática é visivel num escopo local , mas ela é inicializada apenas uma vez e seu valor não é perdido quando a execução do script esse escopo .

O modificador ``static`` é muito utilizado em funções recursivas , já que o valor de algumas variáveis precisa ser mantido. 

Ele funciona da seguinte forma.

O valor das variáveis declaradas como estáticas é mantido ao terminar  a execução da função . Na próxima execução da função , ao encontrar novamente a declaração com __static__ , o valor da variável é recuperado.

In anothers words , uma variável declarada como ``static`` tem o mesmo "tempo de vida" que uma variável global , porém sua visibilidade é restrita ao escopo local em que foi declarada e so é recuperada após a declaração.

Exemplo :

```
	function teste() {
	echo "$a";
	static $a = 0;
	a++ ;
	}
```

---
<h2>Armazenando valores enviados pelo formulario em arrays</h2>

Cada elemento de um formulario HTML submetido a um script PHP cria no ambiente do mesmo uma variavel cujo nome é o mesmo nome do elemento Por exemplo: um campo definido como:

	<input type="text" name="endereco">

Ao ser submetido a um script PHP fará com que seja criada uma variável com o nome $endereco . Isto acontece de forma semelhante para cookies , como veremos mais adiante.

Uma boa técnica de programação é utilizar notação de arrays para nomes de cookies ou itens de um formulário html. Para um conjunto de checkboxes , por exemplo , podemos utlizar a seguinte notação :

	<input type="checkbox" name="teste[]" value="valor1">opcao1
	<input type="checkbox" name="teste[]" value="valor2">opcao2
	<input type="checkbox" name="teste[]" value="valor3">opcao3

Ao submeter o formulário , o script que recebe os valores submetidos terá uma variável chamada $teste contendo os valores marcados num array , com índices a partir de zero. Assim , se forem marcadas as opçoes 2, 3 e 5, podemos seguinter afirmações

```
	$teste == array("valor2" ,"valor3", "valor5");
	$teste[0] == "valor2";
	$teste[1] == "valor3";
	$teste[2] == "valor5";
```
---
<h2>Verificando se uma variável possui um valor</h2>
Existem dois tipos de teste que podem ser feitos para verificar se uma variável está setada : com a função ``isset`` e com a função ``empty``.

###### A função isset

Possui o seguinte protótipo :

	int isset(mixed var);

E retorna `true`  se a variável estiver setada (ainda que com uma string vazia ou valor zero) , e false em caso contrário.

###### A função empty

Possui a seguinte assinatura:

	int empty(mixed var);

E retorna `true` se a variável não contiver um valor (não estiver setada) ou possuir valor 0 (zero) ou uma string vazia. Caso contrário , retorna `false`


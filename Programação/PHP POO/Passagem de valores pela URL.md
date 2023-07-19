Bem , precisamos entender agora como fazer passagem de valores pela URL do site para que possamos pegar algum valor de vindo de outra pagina.

Temos duas formas de fazermos isso a primeira e criando um link de HTML no PHP e fazer a concatenacao da variavel que queremos enviar , e depois na pagina que queremos capturar essa informacao criaremos uma variavel armazenando o valor passado com o metodo __GET__

Por exemplo : 
 ```
	 <?php
$texto = "aqui vai a informacao que vamos pegar na outra pagina";
// aqui vamos mostrar um link criado em HTML para o usuario
echo "<a href=pg1.php?tx=".$texto." target=_self_">Abre a pg1<a/>;

```
Oque fizemos ali foi criar o link para a pagina que queremos e entao colocamos o -> "?" <- esse ponto de interrogacao significa que vira valores apos ela entao nos concatenamos com o " . " e escrevemos o nome da variavel . Obviamente por questoes de seguranca , nunca iremos colocar a variavel junto com o link , ela poderia ficar visivel para qualquer um.

Continuando Agora no nosso outro arquivo chamado pg1;

```
	// aqui vamos armazenar o valor em uma variavel o valor que pegamos com o metodo GET..

	$valorRecebido = $_GET[`tx`];

	// mostramos o seu valor
	echo $valorRecebido;
```

A segunda maneira de fazer a passagem de valor pela URL
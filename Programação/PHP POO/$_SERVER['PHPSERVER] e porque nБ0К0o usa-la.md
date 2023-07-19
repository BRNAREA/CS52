## Variavel _$SERVER[PHPSERVER]

Quando você insere  qualquer variavel no HTML , a menos que você queira que o navegador para interpreta-la si-mesma como HTML , é melhor usar o `htmlspecialchars()` nele . Entre outras coisas, isso previne __hackers__ de inserir HTML arbitrario nele.

O valor de _S$ERVER['PHP_sERVER' ]_  é obtido diretamente da URL inserido no navegador.

	Portanto se você não usar htmlspecialchars() , você permite hackers de manipular diretamente a saída do seu codígo.

Por exemplo , se eu te enviar um link para '<http://exemplo.com/'> <'script'>codigo_malicioso_aqui()<'script'><'span class=''> e você tiver <"form action = " ?php echo $SERVER['PHP_sELF']?> , a saida será

<'form action = "http://exemplo.com/"><'script'>codigo_malicoso()<'script'><'span classes'>
# Web Storage ou Armazenamento Web

É um tipo de armario onde todas as informações passadas por um formulario atraves de um submit serão salvas no navegador do usuario e do servidor , fazendo essas informações serem úteis para vario tipos de coisas como :

[[Preferencias do Usuario]] -> Ex: Preferencia na cor de background do site , Tipos de gostos sobre músicas que podem ser recebidos e varias outras coisas.

Existe também [[sessionStorage.js]] onde o conceito é basicamente o mesmo somente mudando algumas coisas.

### O Mundo não é somente flores
Como nem todo jardim é verde ou todo ceú é estrelado nosso Web Storage também não escapa do ecossistema falho e infeliz . Vamos citar algums Prós e Contras de se usar Web Storage talvez falemos um pouco sobre [[Cookie]]..

Prós :
-   Suporte pela maioria dos navegadores modernos
-   Dados persistentes que são armazenados diretamente no navegador
-   Regras de mesma origem se aplicam a dados de armazenamento local
-   Não é enviado com todas as solicitações HTTP
-   ~ 5 MB de armazenamento por domínio (que é 5120 KB)

Contras:
-   Não suportado por nada antes: IE 8, Firefox 3.5, Safari 4, Chrome 4, Opera 10.5, iOS 2.0, Android 2.0
-   Se o servidor precisar de informações do cliente armazenadas, você deverá enviá-las propositalmente.
<h2> Problemas:</h2>

<section>
	<p> Web Storage (localStorage/sessionStorage) é acessivél através de JavaScript no mesmo dominio . Isso significa que qualquer JavaScript executado em seu site terá acesso ao armazenamento na Web e , por isso pode ser vulnerável a ataques de scripts entre sites <b>(XSS)</b>. O XSS em poucas palavras é um tipo de vulnerabilidade em que um invasor pode injetar JavaScript que será executado em sua página. Ataques XSS básicos tentam injetar JavaScript por meio de entradas de formulário, onde o invasor coloca <code> alert('XSS Detectado')</code>; em um formulário para ver se ele é executado pelo navegador e pode ser visualizado por outros usuários.
	</p>
	
	<h2> Prevenções :</h2>
		<p> 
				Para evitar XSS , a resposta comum é escapar e codificar todos os dados não confiáveis. Mas isso está longe de ser a história completa . Em 2015 , os aplicativos Web modernos usam JS hospedados em CDN's ou infraestruturas externa. Os aplicativos da web moderno incluem bibliotecas JS de terceiros para testes A/B , Análise de funil/mercado e anúncios. Usamos gerenciadores de pacotes como Bower Para importar o Código de outras pessoas para nossos aplicativos.
			
				E se apenas um dos scripts que você usar estiver comprometido ? JavaScript malicioso pode ser incorporado na página e o armazenamento da Web fica comprometido . Esses tipos de ataques XSS podem obter o armazenamento da Web de todos os que visitam seu site, sem conhecimento deles . É provavelmente por isso que várias orgs aconselham a não armazenar nada de valor ou confiar em qualquer informação no armazenamento da Web . Isso inclui identificadores de sessão e tokens.

				Como mecanismo de armazenamento, o Web Storage não impõe nenhum padrão seguro durante a transferencia. Quem lê o Web Storage e o usa deve fazer devida diligência para garantir que sempre envia o JWT por HTTPS e nunca por HTTP.
		</p>
</section>

### Seria então como um cookie?
# localStorage
O metodo <b>[localStorage]</b> é usado para guardar informações de envio de forms em modo de chave e valor. Sendo diferente do [[sessionStorage.js]] , O usúario pode através de um formulario passar certas informações que serão salvas em uma armazenamento reservado pelo navegador .

Com  `localStorage`  o , os aplicativos da Web podem armazenar dados localmente no navegador do usuário. Antes do HTML5, os dados do aplicativo precisavam ser armazenados em cookies, incluídos em todas as solicitações do servidor. Grandes quantidades de dados podem ser armazenadas localmente, sem afetar o desempenho do site. Embora  `localStorage` seja mais moderno, existem alguns prós e contras em ambas as técnicas.

`localStorage`  o uso é quase idêntico ao da sessão. Eles têm métodos praticamente exatos, então mudar de sessão para  `localStorage`  é realmente uma brincadeira de criança. No entanto, se os dados armazenados forem realmente cruciais para o seu aplicativo, você provavelmente usará cookies como backup caso   `localStorage`  não esteja disponível. Se você quiser verificar o suporte do navegador para  `localStorage` 

Essas informações podem ser criadas , alteradas e exlcuidas . Elas não são deletadas quando o navegador é fechado ou até mesmo quando o computador é desligado , permanecendo assim no navegador. Veja Um pouco sobre Web Storage em [[Web Storage Explain]]

O localStorage só pode ser lido pelo <b>lado do cliente</b>

Temos três atributos à partir do método [localStorage] , são eles :
 [setItem()] -> usado para adicionar chave e valor no Storage , precinsado de 2 parametros do tipo [String] (chave , valor);
 
 [removeItem()] -> usado para remover chaves e valores setados pelo atributo [setItem()]
 
 [getItem()] -> usado para obter chaves e valores do método [localStorage].
 
 Agora vamos fazer um pequeno exercicio.. Um contador de visitas
 
 # Primero vamos verificar se o navegador do usuario aceita localStorage dseguinte maneira
 
 <code>
 <script>
	
	if(typeof(Storage) !== "undefined" || "null" || void(0))
	{
		
	}
	else {

            document.write("seu navegador não tem suporte para WebStorage :(");
        }
</script>
 </code>
Agora verificamos se o usuario acessou o site :

 <code>
<script>
	
	 if(typeof(Storage) !== "undefined" || "null" || void(0))
	{
		if(localStorage.visitas) {
			localStorage.visitas = Number(localStorage.visitas) + 1
		}
		else {
			/Podemos fazer de duas maneiras : 
			localStorage.setItem("visitas", 1); OU 
			localStorage.visitas = 1;
		}
		/ E imprimimos na tela quantos usuarios acessou o site com 
		document.write("Você teve :" + local.Storage.visitas + "no seu site");
	}else {
		document.write("Seu navegador não é compativel com Armazenamento Local , :(")
	}
</script>
</code>

Na verdade é bem simples oque aconteceu aqui foi que declaramos um localStorage com um atributo "visitas" : Codigo -> localStorage.visitas , poderia ser qualquer nome mas deixei bem especifico para o seu entendimento , podemos fazer criar outros atributos tambem depende da sua criativadade .. continuando ..

o IF verifica se existe o atributo localStorage.visitas , se for a primeira vez do usuario no site então não irá existir , então o codigo ira cair no Else que criará para gente o atributo de fato , com o valor inicial de 1 já que é a primeira vez do usuario
 <code>
<script> 
	else {
			/Podemos fazer de duas maneiras : 
			localStorage.setItem("visitas", 1); OU 
			localStorage.visitas = 1;
		}
</script>
</code>
Você lembra que o localStorage fica armazenado no navegador até que alguem o remova?? ele ficará eternamente até que o usuario decida deletar ou o programador delete de fato, então com o site visitado , toda vez que o usuario entrar a contagem aumentará em 1 , o código irá cair no IF que fará a incrementação.
 
<code>
<script> 
if(localStorage.visitas) {
			localStorage.visitas = Number(localStorage.visitas) + 1
		}
</script>
 </code>	
 E depois Imprimimos na tela
 
<code>
 <script>
document.write("Você teve :" + local.Storage.visitas + "no seu site");
</script>
</code>	
Facil é .. mas tem que prestar muita atenção. Porém tudo tem seus problemas vamos citar alguns prós e contras na sessão [[Web Storage Explain]]

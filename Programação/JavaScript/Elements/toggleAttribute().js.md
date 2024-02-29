# toggleAttribute()

## removeAttribute() vs toggleAttribute() qual usar e quando usar ?

Bom antes de saber qual dos dois usar , temos que saber para qual fim serve o metodo [toggleAttribute()] Então vamos para a definição desse método.

<h3>Entendendo o funcionamento do método </h3>
	<section> 
		<p>toggleAttribute() é um método de <b>definição dinamica para um elemento</b> , ou seja ele proprio coloca o atributo se o elemento não o conter ou remove se ele tiver o atributo </p>
	
	<p>Mas isso ficaria estranho se não colocar uma função para tal método não é verdade ? não teria sentido nenhum e só causaria bugs e falhas no nosso código..
	
	Por isso é sempre bom seguir pequenos preceitos que o método necessita .. 
	1) Usar em funções
	2) Usar quando você tiver muitos elementos..
	3) Usar somente se você quer que algo mude dinamicamente
	
	Isso porque o proprio elemento já faz isso por nós e digo mais..Não teria sentido em usar somente em um ou dois elementos compensaria usar o método [[removeAttribute.js]]</p>
	</section>
	
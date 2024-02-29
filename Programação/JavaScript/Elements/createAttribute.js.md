# createAttribute

## como criar um atributo para um elemento no Javascript ?

 Bom primeiro de tudo , temos que  ter em mente quais elementos queremos criar um atributo , então necessariamente temos que resgatar o elemento com o metodo :  `getElementById('elemento')`  a partir disso precisamos criar o atributo .. vamos dizer que eu queria o atribute `style` então eu crio ele da seguinte maneira : 
 

	var elementoResgatado = document.getElementById("tag do elemento"); 
	
	// aqui criamos um atributo chamado style , mas tambem poderia ser outros como : readonly , input e etc..
	var attr = document.createAttribute('style'); 
	
	E então definimos o valor do atributo atraves da variavel e do mateodo .value
	
	attr.value = "color : red"
	
	// depois adicionamos o atributo para o elemento com o meotodo : setAttributeNode() da seguinte forma
	
	elementoResgatado.setAttributeNode(attr); -> aqui colocamos o atributo style que criamos na variavel attr e colocamos juntamente da variavel elementoResgatado.


Agora que ja sabemos como criar um atributo o valor dele e atribui-lo no elemento precisamos tambem saber como remove-los . Mas isso você pode olhar no indice [[removeAttribute.js]] 

Você tambem pode aprender a criar elementos na seção [[createElement.js]] e adicionalos em uma tag na seção [[appendChild.js]]


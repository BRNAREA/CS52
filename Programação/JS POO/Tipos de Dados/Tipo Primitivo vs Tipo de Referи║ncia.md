# Qual a diferença entre Primitivos e Tipo de referência ?

A diferença entre eles está na forma de como eles são armazenados na memoria

Quando criamos algum tipo primitivo que pode ser uma `string` ou `number` por exemplo , e a gente atribuí a esse tipo uma varíavel ou constante , esse valor é armazenado em um lugar que a gente chama de `STACK` ( a trudução literal para stack seria pilha )  e esses valores podem ser acessados rapidamente quando a gente precisa usar eles.

So que o espaço dentro dessa stack é limitado , então quando a gente cria um tipo de referência como um Objeto ou Array esse tipo ao ínves de ser armazenado na stack vai ser armazenado no `HEAP`  ( a tradução literal para heap seria amontoado )

O `Heap` tem mais espaço disponivel para que seja armazenados objetos maiores e mais complexos como Objetos Literais e Arrays , mesmo sendo um pouco mais lento de ser acessado .


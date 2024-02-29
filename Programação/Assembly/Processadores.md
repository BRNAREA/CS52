

Por volta de 1990 ,existia um processaador fabricado pela Intel, e ele é conhecido por 386 .O Linus ,parece ,quando lançou o primeiro kernel do Linux,,  
parece que estava usando esse processador .O kernel do Linux na época rodada nesse tipo de processador ( ou clones ) .Por volta de 1993, começaram a surgir os processadores da Intel com o nome de 486 .Eram ma,is rapidos que os 386 ,e a Intel tinha modificado um pouco o processador ,então o kernel do Linux teve que se adaptar a esse novo processador ,assim como tb os programas que rodavam no Linux .Programas com otimização para o 486 ,passaram a chamar "i486 ".O kernel do linux continuava a rodar em proc 386,  
mas podiam ser otimizados para os novos processadores 486 ,assim como os programas .Já ,por volta de 95 a Intel anunciou que um novo processador iria ser lançado,mas não disse o nome .Os outros fabricantes ,(Cyric ,AMD,etc) pensaram que esse novo processador iria se chamar 586 ,daí  
surgiu essa nomenclatura ,mas em vez disso a Intel lançou o proc de nome  
Pentium .O kernel então teve que se adaptar a essa nova versão de processadores ,daí a designação i586 .Depois vieram os Pentium 2 ,os quais  
receberam o nome de i686 .Kernel adaptado tambem para rodar no Pentium 2  
( ou seja nos i686).Todos os Kerneis do LINUX rodam em processadores desde os 386 .Quando compilamos o Kernel podemos otimizar o nucleo para  
um determinado processador .Por exemplo se eu otimizar o nucleo para  
um Pentium 1 ( i586) ,o SO não rodara em processador 386 ou 486 ,mas só em processadores Pentium I ,pra cima .  
Todo kernel saido de "fabrica"vem para ser rodado em um processador 386  
Suponhamos que eu tenha otimizado o kernel do meu Linux para o Pentium 2  
( i686),suponhamos tb que estou atraz de um drive , ai eu encontro ,por exemplo:  
xxxxx.i386.tar.gz <---drive a  
xxxxxi486.tar.gz <----drive b  
xxxxxi586.tar.gz <----drive c  
xxxxxi686.tar.gz <----drive d  
Se eu otimizei o kernel para o i686 ,então o melhor drive para mim sera o "d"  
mas isso não quer dizer que os drivers a ou b ou c não rodarão na minha maquina .O drive d já vem otimizado para rodar no meu Pentium 2.  
Por outro lado suponha que eu tenha um processador 486 ,e o linux otimizado para tal proc(486) ,então o drive i686 ,não servira para mim ; Se eu tenho um proc 486 eu só posso instalar ou o drive a ou o b ....

even the difference between accessing memory from a CPU register versus that of the L2 cache can be more than 6 times ! **Memory access is not free, and abstractions have a cost, no matter how insignificant they may seem.**

## Estrutura Básica

A organização de um computador simples com uma CPU e dois registradores de E/S.

![[Processadores 2024-02-21 00.37.38.excalidraw]]

Instruções

1) Trazer a proxima instrução da memória  até o registrador de instrução
2) Alterar o contador do programa para que aponte para a próxima instrução.
3) Determinar o tipo da instrução: soma, multiplicação, leitura ou escrita na memória, mover dados de um lugar para outro etc..
4) Se a intrução usar uma palavra na memória, determinar onde está essa palavra.
5) Trazer a palavra para dentro de um registrador da CPU,. se necessário.
6) Executar a instrução.
7) Voltar a etapa 1.
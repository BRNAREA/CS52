#                     Promise
###### As promises (promessas) simplificam as computações adiadas e assíncronas. Uma promessa representa uma operação que ainda não foi concluída.


Uma promessa pode ser:

- __cumprida__ (fulfilled) - a ação relativa à promessa foi bem-sucedida
- __rejeitada__ (rejected) - a ação relativa à promessa falhou
- __pendente__ (pending) - ainda não cumprida ou rejeitada
- __resolvida__ (settled) - cumpriu ou rejeitou

<u> A especificação </u> também usa o termo __thenable__ para descrever um objeto que é semelhante a uma promessa , no sentido que possui um método ``then`` .

As promessas do JavaScript compartilham um corportamento comum e padronizado chamado <u> Promises/A+ </u>. Semelhante ao <u> Deferreds </u> do jQuery. No entanto , os Deferreds não são compatíveis com Promise/A+ , oque os torna sutilmente diferentes e menos úteis.

Veja como criar uma promessa usando JavaScript em [[new Promise]]

O construtor <u> Promise </u> recebe um arugmento , que é um _callback_ com dois parâmetros , [[ resolve]] e [[rejected]] , acima.

Faça algo dentro do callback , talvez algo assíncrono , e depois chame resolve() se tudo certo ; caso contrário , chame reject();

Assim como ``throw`` no JavaScript clássico , é comum , mas não obrigatório , chamar reject() com um objeto Error. A vantagem dos objetos Error é que eles capturam um rastreamento de pilha , facilitando a vida das ferramentas de depuração.

Veja como usa poderiamos usar essa promessa em [[then]] e [[catch]]

O JavaScript executa o seu código de cima para baixo em thread única ou seja se houver um código sincrono com uma função que demora 10 segundos para obtermos a resposta essa função estagnaria todo o restante do código abaixo impedindo o funcionamento de toda a execução do código abaixo. 

Um código assíncrono pode iniciar um processo agora e finalizar esse processo posteriormente sem impedir que o restante do código seja travado

Outro ex de código assincrono é uma requisição.

Quando queremos pegar alguns dados da API do Youtube você precisará fazer um request e esse request é assíncrono . Porque?

Por que essa operação vai ser passada passa uma thread separada e o código que você escreveu depois desse request vai continuar executando as próximas funções que ele tem que executar

Mas o JavaScript não é uma thread única ?

>[!ATTENTION]
>O JavaScript que __você__ escreve é executado em thread única , mas o request , requisições  , são entregues para uma thread separada que é executada fora da Thread do JavaScript é isso faz com que o restante do seu código continue sendo executado enquanto esse request é processado.

![[Pasted image 20220804133242.png]]

Ao usar `Promises` nosso código ganha três vantagens que merecem Destaque.

A primeira vantagem é que ganhamos mais controle e legibilidade no fluxo de lógicas assíncronas 

A segunda é que reduzimos o acoplamento entre funções de callback

A terceira é que temos mais previsibilidade detalhamento no tratamento de erros.



# Explicando o protocolo HTTP
## Hiper Text Transfer Protocol
O Hiper Text Transfer Protocol (HTTP) , é um tipo de protocolo da internet para envio de informações requisitadas pelo cliente ao servidor .



Pórem precisamos entender o caminho que ele faz ate chegar ao servidor , ou melhor precisamos entender como faz para ele chegar ao servidor então explicarei abaixo como funciona em suma.

### Rota de informações em HTTP

Bom para que toda informação seja levada para alguem , é necessario fazer uma rota , um caminho , para que seja entregue a informação no geral .. No HTTP essas rotas das requisições passam por **roteadores ,  gateways , roteadores de proxys , casts e centenas de outros** , o que realmente precisamos saber é que quem traça essas rotas até a requisição chegar ao servidor é o protocolo  , a partir do destinado traçado precisamos do [[Protocolo TCP]] para que nossas informações sejam decidas como serão enviadas , caso haja perda ou desorganização de pacotes quem é responsavel por repor ou reorganizar as informações é esse protocolo.

### Explicando camadas de redes (Simplificada)
Para entendermos o HTTP devemos saber as principais camadas do [[Modelo OSI]] são elas.

- Aplicação
- Transporte
- Rede
- Hardware

- Aplicação aqui roda alguns protoclos como : HTTP , SMTP , DHCP , FTP , aqui é de fato a parte do software , do programa
-  Transporte , cuida de como os arquivos vão ser transportado do cliente / servidor e etc. Protocolos como : TCP , UDP . Estão listos nessa camada
-  Rede , nessa camada roda o protocolo IP , nessa camada é o ecossistema da internet , oque molda ela , como uma informação chegue até seu destino 
-  Hardware , por fim a camada de Hardware que pega a mensagem entregue que transforma em sinais eletronicos que define por quais cabos as informações devem ser enviadas , Endereço MAC esta nessa camada.

### Servidor

Quando enviamos as informações do cliente , essas informaçoes trafegam a internet até chegar nas camadas do servidor que por algum programa do lado do servidor que entende de HTTP.

Mas agora uma duvida nos cai , como tem muitos programas rodando no servidor como ele sabe para qual programa a informação deve mandar ? Para elas serem processadas e terem uma resposta ?

Bem .. 

Vamos dizer que temos 3 pacotes TCP

Para ele ( o servidor ) saber para qual programa  mandar existe o conceito de [[Portas de rede]] , então quando mandamos uma requisição dizemos para o servidor qual porta queremos usar , cada porta roda um protocolo de rede então o protoclo TCP é responsavel por direcionar as informações para a porta correta.

Mas mesmo assim como o programa que está rodando sabe como lidar com essas informaçoes ??? Ex : enviamos um texto e o servidor n sabe como lidar.

E é exatamente para isso que servem os protocolos

O protocolo HTTP tem uma serie de regras , palavras reservadas , métodos estabelecidos de como uma "mensagem " , "informação deve ser entregue por ele" , A informação enviada tem que ser um programa que saiba ler o HTTP , que saiba com ele funciona

Na maioria das vezes os programas usados para ler as informações para o HTTP são : 

- NGINIX
- Apache
- Tomcat
- Node

E agora que as informações foram entregues  , tratadas , lidas , o servidor retorna como uma respostas **tambem em HTTP** , e então o seu navegador que sabe mais como ninguem , interpretar o HTTP e vai tomar providencias com a resposta dada do servidor.

## HTTP Headers
O HTTP é um protocolo de requisição e resposta . E agora vamos ver como são passados essas requisições e respostas através dos __Headers do HTTP__ .

![Headers](data:image/png;base64,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).

---

### Request Header
> [!INFO]
__Linha de Pedido__
>*A linha de pedido é composto pelo método , ex : GET , POST , DELETE ETC..*
>Depois precisamos falar qual o recurso ele vai acessar ex : /contato , / post etc.. e por fim a Versão que será usada ex: HTTP/1.0
>![Métodos](https://miro.medium.com/max/808/1*afUW6IXbXCP1mD8OaS906w.png)
>---
>__Cabeçalhos gerais__
>*Composto pelos Headers como : Date , Pragma , Cache-Control , Connection , Trailer , Transfer-Enconding , Upgrade	 , Via , Warning.*
>![Cabeçalho Geral](https://2286696559-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-MVRn4REfCrgOC5oEZbZ%2F-MhJLgkutsiv3sMJHc_X%2F-MhJcWNyf8Xd24ODrNeM%2FHTTP-request.png?alt=media&token=2c28c814-fbc5-4029-9053-8288ff748116)
>---
>__Cabeçalhos do pedido__
>Há muitos cabeçalhos no Cabeçalhos de Pedidos por isso iremos citar apenas 4 mais importantes.
>- Preferencia de Resposta : Accept || Accept-language || Accept-Charset 
>É a respotas desejada que seja enviada de volta , é a preferencia que seja enviada como resposta .
><br>
>- Informações enviada com o pedido : Informações como -> User-Agent , From , Authorization etc
><br>
>- Pedido Condicional : Proxy-Authoization || If-Modified-Since || If-Range estão contidos nesse cabeçalho
><br>
>- Restrição no Servidor : É o de fato o Host o dominio
>---
>__Cabeçalhos de entidade__
>Aqui são definidos tipos e metodos de como as informações serão passadas . Métodos usados nesse cabeçalhos como : Allow || Content-Type, Content-Language são usadas para definir como serão enviadas o contéudo.
>Ex: **Content-Type : text/html ; Content-Lenght: 50**
>---
>__Entidade e Recurso__
>Ex: nome=Ayrton&email=progrmadorabordo%..
>---

## Response
>[!INFO]
>__Linha de Status__
>É formado pelo versão do HTTP , O número do Status veja a lista dos numeros de status disponiveis no site da [Mozila](https://developer.mozilla.org/en-US/) Na aba de [Status Response](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status)
>---
>__Cabeçalhos Gerais__
>Como ja vimos em acima.
>---
>Cabeçalhos de Resposta
>- Informação : Server ||  Retry-After || Accept-Ranges
>- Segurança : WWW-Authenticate | Proxy-Authenticate
>- Cache : Etag | Age | Vary
>---
> __Cabeçalho de Entidade__
> Conteúdo que estamos devolvendo
> ---
> __Entidade/Recurso__
> Content-Type , JSON
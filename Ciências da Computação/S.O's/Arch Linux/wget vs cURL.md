wget -> Uso comuns : Baixar webpages ou arquivos
`wget https://file-examples.com/wp-content/uploads/2017/02/file-simple_100kb.doc`

O Arquivo é recuperado e salvo no seu computador com nome original

![[Pasted image 20220919213418.png]]

Para salvar o arquivo baixado com um novo nome , use o `-O` *output document*.

Não use a opção `-O` quando você for recuperar websites . Se fizer isso , todos os arquivos recuperados vão se juntar em um só.

Para trazer um website inteiro , use a opção `-M` (mirror) e a URL do website. Você tambem vai querer usar `--page-requisites` para ter certeza que todos arquivos de suporte necessários para renderizar corretamente as páginas da Web também sejam baixados. A opcao  `--convert-links` ajusta os links no arquivo recuperado para apontar para os destinos corretos em seu computador local em vez de locais externos no site.


cURL -> é um projeto de fonte-livre independente. 

Para baixar os mesmo arquivos que fizemos com `wget` , e salva-los com o mesmo nome , precisamos usar este comandp . Note que o `-o` (output) esta em lowercase com `cURL`.

O arquivo esta sendo baixado para gente. Uma barra de progresso em ASCII e mostrado durante o download.

![[Pasted image 20220919232248.png]]

Para conectar em um servidor FTP e baixar um arquivo , usamos a opcao `-u` (*user*) e passamos um par de usuario e senha , tipo assim :

`curl -o teste.png -u demo:password ftp://test.rebex.net./pub/example/KeyGenerator`

Isso vai baixar e renomear o arquivo de um servidor FTP teste.

## Quem e o melhor ? 

Simplesmente nao existe melhor.

Depois de entender o que o `wget` e o `cURL` fazem , voce percebera que eles nao estao competindo. Eles nao atendem ao mesmo requisitos e nao estao tentando fornecer a mesma funcionalidade. 

O download de paginas da web e sites e onde esta a superioridade do `wget`. Se e isso que voce esta fazendo use `wget`. Para qualquer outra coisa - Fazer upload , por exemplo , ou usar qualquer um dos inumeros outros protocolos - use `cURL`.


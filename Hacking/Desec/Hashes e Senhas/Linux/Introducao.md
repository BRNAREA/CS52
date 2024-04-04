<h1 align="center"> Entendendo os Hashes</h1>
<hr>

Neste modulo iremos falar sobre Hashes ,

Eh muito importante entender como um Hash funciona , oque eu um hash , como gerar hashes , porque em diversos momentos iremos nos deparar com eles e precisaremos identificar um hash , atacar um hash enfim .. existem varias tecnicas.

```ad-question
title: Oque eh um hash?

Um hash seria um tipo de encript para algo , podendo ser um executavel , arquivo , textos planos e etc..

Um hash sempre sera aleatorio mas sempre tera um tamanho fixo
Exemplo hash MD5
`28f2b95533afb47cbec1d823b0f1a941`

Exemplo hash SHA 512
`2385bd1542542aac275db5f88b8e3f788145c773da97a137131ac5433c0b9ed41f9704ff1a431f8473b6b82f9da963a270029a818bcfb299c857174b73a61a89`

Essas duas saidas sao de tipos de diferentes , porem de uma mesma palavra ("algo") no nosso caso.

```

<h2 align="center"> Exemplo de uso: Autenticacao</h2>
<hr>

Ao se cadastrar em uma aplicacao essa aplicacao pedira sua senha e por boas praticas e normas de desenvolvimento , suas credenciais passarao por uma especie de tratamento antes de ser armazenadas em um banco de dados , por padrao de desenvolvimento a sua senha passa por uma especie de `encrypt` podendo ser `SHA512`, `md5`, `SHA1` e por ai vai.

Entao oque fica gravado no banco de dados , eh basicamente sua senha , emaranhada por um tanto de caracteres estranhos de tamanho fixo que ninguem pode entender , mesmo se alguem mal intencionado pegue seus dados ele vera ela toda encriptada e nao na forma de texto plano.

![[mpv-shot0001 11.jpg]]


```ad-question
title: Como funciona?

Ah , mas como a aplicacao vai saber que ao digitar minha senha ela eh igual ao banco de dados , sendo que no banco de dados esta toda encriptada e nao seria igual a senha digitada?


Bem , ao digitar sua senha oque a aplicacao faz eh aplicar o hash no valor inserido no caso sua senha suponhamos um SHA256 , oque ele gerar vai ser comparado ao banco de dados para verificar a integridade e autenticidade da senha , se forem os mesmo hashes o usuario eh logado na aplicacao.

Ate porque as funcoes de hashes NAO sao reversiveis , elas sao One-Way hashes , onde voce nao consegue desreverter aquele hash basicamente.
```

<h2 align="center"> Exemplo de uso: Integridade</h2>
<hr>

Quando voce tem um programa ou arquivo oficial, eles costumam ter uma especie de `checksum` um hash unico tirado daquele software , se qualquer outro programa malicioso por mais que altere algum BYTE quer sera gerado um hash completamente aleatorio do oficial , entao isso verifica a integridade daquele programa/arquivo/software.

![[mpv-shot0002 10.jpg]]



<h2 align="center">Directory Browsening ou Listagem de Diretorios </h2>
<hr>

```ad-important
Ma configuracao do servidor web , onde nao ha presenca de arquivo index no diretorio raiz.
```

```ad-question
title: Como mitigar essa falha?

Para mitigar isso poderiamos simplesmente configurar o servidor apache se for o caso em :
"/etc/apache2/apache2.conf"
```


editando a linha na qual permite essa listagem de arquivos e diretorios caso nao haja um index.html.

```apache2.conf
<Directory /var/www/>
	Options Indexes FollowSymLinks
	 AllowOverride None
	 Require all granted
</Directory>

Para:
<Directory /var/www/>
	Options FollowSymLinks
	 AllowOverride None
	 Require all granted
</Directory>

```


Removendo a linha "Indexes"..
Isso fara com que nao liste os arquivos e diretorios se nao houver um index.html 

E reiniciamos o apache

`service apache2 restart`

<mark style='background:var(--mk-color-purple)'>Um outro erro comum em servidores apache</mark>

<mark style='background:var(--mk-color-purple)'>Seria ao fazer uma requisicao invalida</mark> no nosso caso vamos fazer em 172.18.0.1/requisitandoumarquivoinexistente.txt

O servidor retornara no Browser a seguinte maneira
# Not Found

The requested URL was not found on this server.

---

Apache/2.4.58 (Debian) Server at 172.18.0.2 Port 80


Isso nao eh legal pois podemos ver qual o servico que estamos utilizando alem da versao dele no caso : Apache versao 2.4.58 , tambem podemos ver o sistema que eh o Debian o IP do servidor no caso : 172.18.0.2 na porta 80

Para mitigarmos isso podemos fazer outra configuracao no apache em 

`"/etc/apache2/conf-enabled/security.conf"`

A linha "ServerTokens" esta em OS , na qual faz esse disposicao de informacao para o usuario, vamos mudala para "Prod" para o minimo de informacao possivel

ServerTokens Prod

Tambem podemos tirar a lihna de Assisnatura do servidor ou ServerSignature

<mark style='background:var(--mk-color-purple)'>ServerSignature Off</mark>

E reiniciamos o servidor apache

`service apache2 restart`
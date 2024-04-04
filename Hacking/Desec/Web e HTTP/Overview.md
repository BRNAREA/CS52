A internet funciona por meio de um cliente e servidor atraves de um protocolo da internet chamado HTTP (Hyper Text Transfer Protocol).

Cliente = Browser (Navegador)
Servidor = Apache , NGINX etc..

Ao fazer uma requisicao feita pelo cliente o servidor retorna com uma resposta se foi bem sucedida ou mal sucedida.

Quando esta resposta eh retornada para o Cliente (Navegador) ela geralmente vem com um STATUS CODE , um status code seria um numero para identificar a resposta como:

```http
200 OK
404 Not Found
403 Forbidden
303 Moved Permanently
```

O servidor apache geralmente tem seu diretorio por padrao em "/var/www/html/" , onde se encontra todos os arquivos como "indx.html", "index.css" , diretorios importantes e outros...

Mas isso seria uma falha de seguranca por que quando voce acessa o servidor do apache sem ter um index.html , ele listara todos os diretorios e arquivos disponiveis , e isso seria uma vulnerabilidade chamada de "Directory Browsing" na qual ele permite a outras pessoa a acessarem os diretorios e arquivos importantes do servidor .

```ad-seealso
title: Veja essa vulnerabilidade em Vulnerabilities
[[Directory Browsening]]
```

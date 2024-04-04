<h2 align="center"> Sender Policy Framework</h2>
<hr>

```ad-question
title: Qual o objetivo do SPF? 
Basicamente identificar quais servidores estao atualizados a enviar email em nome do seu dominio , isso eh importante porque se voce nao tiver a configuracao de SPF configurada no seu dominio ou esta configuracao esta mal feita , qualquer pessoa consegue fazer email spoofing atraves do email da empresa , ou seja falsificacao do email daquele dominio

Visa identificar quais servidores estao autorizados a enviar emails em nome do seu dominio.
```


Ex:

| SPF                                               | Sender Policy Framework                 |
| ------------------------------------------------- | --------------------------------------- |
| **v=v=spf1 include:servidorpermitido.com ?all**   | *suscetivel (neutro)*                   |
| **v=spf1 include:servidorpermitido.com (til)all** | *suscetivel (eh tratado como suspeito)* |
| **v=spf1 include:servidorpermitido.com -all **    | *Configuracao Recomendada*              |
| **Sem registro SPF**                              | *Vulneravel a Mail-Spoofing*            |

Como a gente pode validar isso?

A primeira coisa que a gente faz  eh olhar os registros txt do servidor:

```sh
host -t txt businesscorp.com.br
```

Se este comando nao retornar nada  , significa que nao tem configuracao SPF , entao pode estar vulneravel de cara.

![[mpv-shot0003.jpg]]
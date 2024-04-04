<h2 align="center">Aquisicao de subdominio </h2>
<hr>

```ad-question
title: Oque eh subdomain Takeover?
Essa eh uma tecninca bem interessante  tanto em pentest quanto bugbounty muito utilizada e bem paga.

Isso porque toma controle de um subdominio de uma empresa e por esse dominio ser real de uma empresa voce pode criar um cenario de fraude para os clientes daquela empresa ou pra criar um ataque especifico para os funcionarios da empresa , uma vez que voce ta com o subdominio da empresa.

```

![[mpv-shot0004.jpg]]

```ad-question
title: Como funciona este ataque?

Quando a gente registra o dns , temos la todos os registros incluindo o **CNAME** (um alias para outro endereco)

entao por exemplo suponhamos que temos o dominio <mark style='background:var(--mk-color-purple)'>doc.businesscorp.com.br</mark> com o CNAME para <mark style='background:var(--mk-color-teal)'>businesscorp.github.io</mark> entao quando voce tenta acessar <mark style='background:var(--mk-color-purple)'>doc.businesscorp.com.br</mark> ele esta acessando o servico la no github (<mark style='background:var(--mk-color-teal)'>businesscorp.github.io</mark>)
```
![[mpv-shot0005.jpg]]
```ad-question
Mas ate ai nao vimos problema,
O problema esta no cenario (terceiro da imagem) na qual tem um subdominio
<mark style='background:var(--mk-color-green)'>dev.businesscorp.com.br</mark> onde o <mark style='background:var(--mk-color-charcoal)'>CNAME</mark> dele aponta para <mark style='background:var(--mk-color-purple)'>businesscorp.s3.amazon.com</mark> , aqui temos um problema porque este servico esta desativado , a entrada de DNS foi criada mas o servico que a empresa utilizava foi desativado, a partir do momento que a empresa parou de utilizar o servico , na amazon por exemplo aquele nome de servico que um dia foi registrado pela empresa , fica disponivel novamente e por isso eh uma aquisicao de subdominio.
```


![[mpv-shot0006.jpg]]


```ad-bug
title: Como a gente detecta essa vulnerabilidade?
- O registro DNS aponta para um servico desativado
- host -t cname doc.businesscorp.com.br                      <- Brute Force DNS
- doc.businesscorp.com.br APONTA PARA businesscorp.github.io
```

![[mpv-shot0007.jpg]]

<h5 align="center"> Criando um script para subdomain takeover</h5>
<hr>

```sh
#!/bin/bash
for palavra in $(cat lista.txt);do
host -t cname $palavra.$1 | grep "alias for"
done
```

![[mpv-shot0008.jpg]]




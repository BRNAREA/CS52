<h2 align="center"> Mapeando a Infraestrutura por IP</h2>
<hr>

A primeira coisa que precisamos fazer eh descobrir o endereco IP do alvo, o endereco IP correto.

Podemos fazer de tres formas, com resultados diferentes para que possamos entender quais informacoes sao importantes nessa fase.

Forma 1:
A primeira coisa e descobrir o IP do host com o comando `whois`, oque buscamos nessa consulta ? Descobrir o netblock ou o ASN do cliente.

Se o cliente tiver o netblock , ok matamos a jogada mas tem alguns casos que o cliente vai usar algum proxy , algum servico para ocultar o endereco IP real dele , e ai podemos acabar nos confundindo , para isso fazemos

```bash

host businesscorp.com.br
businesscorp.com.br has address 37.59.174.225
businesscorp.com.br mail is handled by 10 mail.businesscorp.com.br.

arin.net ou whois no terminal
whois 37.59.174.225 | egrep "inetnum|aut-num"


```

Caso venha um ip diferente sempre identifique essa informacoes

```sh
inetnum:     200.196.144.0/20
aut-num:     AS15256
abuse-c:     INI74
owner:       Itau Unibanco S.A.\
NetName:     ...

```

Entao tente consultar os subdominios

```sh
host post01.itau.com.br
```
```ad-info
title: whois
O whois eh um protocolo que funciona na porta 43 TCP
```

Para pesquisar o bloco de rede de alguma empresa vamos no primeiro lugar a se comecar... no whois da IANA

Pesquisamos sobre o alvo `businesscorp.com.br` e vemos o campo `referer` ,  onde fala o endereco pra fazer a pesquisa , no caso `whois.registro.br` 

Entao vamos ate `whois.registro.br` e pesquisamos `businesscorp.com.br` , agora sim . ele nos traz as informacoes corretas.

Agora pegamos o endereco IP do DNS e jogamos de volta no whois da IANA.
Pegamos o `referer` a vamos atras
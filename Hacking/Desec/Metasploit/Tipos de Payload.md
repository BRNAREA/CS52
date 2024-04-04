<h2 align="center"> Teoria: Tipos de Payloads</h2>
<hr>

De acordo com cada xploit que a gente carrega dentro do metasploit nos temos diversos tipos  de payloads que podemos utilizar , entao eh interessante a gente enteder a caracteristicas de cada payload.

![[mpv-shot0001 8.jpg]]

A primeira parte eh relacionada ao tipo  de sistema que voce vai atacar.
A segunda parte ele vai utilizar um payload do tipo meterpreter.

```ad-info
title: Reverse TCP

Faz uma conexao reversa utilizando  o protocolo TCP ou seja o alvo vai se conectar a nossa maquina
```

 ![[mpv-shot0002 9.jpg]]
Uma caracteristica importante de um payload que voce vai usar eh o Staged e o Inline

Inline / non_staged: Significa que ele eh um payload inteiro , entao quando voce explora a maquina o payload ja eh executado , de uma vez so , ele eh enviado e executado de uma unica vez

Staged: Envia o payload por estagios, codigo por codigo , faz por pequenos pedacos de codigos
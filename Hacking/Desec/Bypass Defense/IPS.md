
<h2 align="center">BLOQUEIO DE PORT SCAN</h2>
<hr>

O software <mark style='background:var(--mk-color-teal)'>Portsentry</mark> vai simular varias portas abertas na nossa maquina (portas falsas)
A ideia desse software eh abrir varias portas e misturar com as portas originais , entao quando alguem tenta fazer um port scanning no seu host , quando ele bater em umas das portas falsas ele dispara uma acao para bloquear o atacante.

```ad-info
title: Arquivo de configuracao

Localizacao: **/etc/porsentry/portsentry.conf**
```

```bash
apt install portsentry

service portsentry start
netstat -lntp

BLOCK_TCP="1"
BLOCK_UDP="1"
#iptables support for Linux
KILL_ROUTE="/sbin/iptables -I INPUT -s $TARGET$ -j DROP"
KILL_HOSTS_DENY="ALL: $TARGETS$ : DENY"

/usr/bin/portsentry -stcp      ;;bloquear stealth scan ou seja nmap -sS
```

Note que quando ha o uso do portsentry no host e tentamos varrer com o [[NMAP]] para pegarmos o banner , ele nos retorna nas portas falsa  a string `tcpwrapped`

<h2 align="center"> ARP</h2>
Identificar hosts ativos com firewall ativado bloqueando o protocolo ICMP ou seja Ping seria inutil no caso.

- Conectado em um ponto de rede (cabo ou wireless)
```ad-warning
title: ATENCAO!
ESTE TIPO DE TECNICA DE IDENTIFICAR HOSTS COM PROTOCOLO ARP SO FUNCIONA EM PENTEST INTERNO OU SEJA , NO LOCAL/SEDE DA EMPRSA.
```

```bash
for ip in $(seq 10 14); do arping -c 1 192.168.0.$ip;done | grep "60 bytes"
```

```bash
arp-scan -l
```


Analisando a rede no tcdump

```sh
tcpdump -vn -i enp3s0 host <IP> and <IP2> -e
```
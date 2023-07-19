
*Antes de entedermos as Classes E e D precisamos saber de algumas informacoes especiais. Segue abaixo.*

***Unicast***: unico na mesma rede.

***Multicast***: varios na mesma rede.

***Broadcast***: Todo os dispositivos da mesma rede.

***Anycast***: qualquer dispositivo mais proximo na mesma rede.

Classe E - Classe de IP do tipo E eh destinado a "teste de novas tecnologias" essa classe serve especificamente para o proposito de uma nova tecnologia de rede . EX: Rede 8G etc..

Classe D - Comunicar com varios dispositivos na mesma rede. ( Multicast )

 ---
<h2 align="center"> IPs restritos / privados (RFC 1918)</h2>
	10.0.0.0/8 - Rede Interna / Local
	172.16.0.0/12 - Rede Interna / Local
	192.168.0.0/16 - Rede Interna / Local

<h2 align="center">IPs reservados</h2>
	127.0.0.0/8 - Loopback/localhost
	169.254.0.0/16 - apipa
	0.0.0.0/8 - IP de inicializacao
	255.255.255.255 - Broadcast geral

```ad-note
title: APIPA
collapse: open
**169.254.0.0/16** ou **APIPA**
Este endereco de IP eh usado em emergencia pelo proprio sistema operacional quando o dispositivo tenta se comunicar com um servidor,modem, DHCP mas nao contem um endereco IP e entao ele configura esse endereco IP automatico pre-estabelecido
 
```

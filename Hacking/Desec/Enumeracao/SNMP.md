<h2 align="center">Simple Network Management Protocol </h2>

<hr>


O SNMP eh um protocolo para gerenciamento de dispositivos na rede , vamos encontrar ele normalmente em roteadores , switchs genreciaveis, equipamentos de rede.. mas tambem em servidores, e quando conseguimos enumeralo , podemos conseguir muita informacao sobre o ambiente, como : informacoes de usuarios , informacoes de programas instalados, portas abertas , e muitos detalhes sobre o sistema operacional

```ad-tldr
title: Protocolo para gerenciamento de dispositivos em rede

Porta padrao: 161(UDP)
```

|                                   |     | Importante                                                       |
| --------------------------------- | --- | ---------------------------------------------------------------- |
| SNMP                              |     | 161 (UDP)                                                        |
| OID - Object Identifier           |     | Codigo utilizado para identificar os objetos                     |
| MIB - Management Information Base |     | Base contendo informacoes relacionadas ao gerenciamento de redes |
| Community                         |     | Valor utilizando entre as partes snmp para troca de informacoes  |

Nivel de acesso (Community)
RO - Read Only - Acesso de leitura
RW - Read and Write - Leitura e escrita


![[mpv-shot0004 3.jpg]]


![[mpv-shot0005 2.jpg]]


Fazendo a enumeracao:

```sh
nmap -sVU -p161 -Pn 172.18.0.2

ou

onesixtyone -c comu.txt. 172.17.0.1

snmpwalk -c public -v1 172.16.1.4 1.3.6.1.4

ou entao instalar o translate para ficar mais facil ao inves de colocar os numeros oid

apt install snmp-mibs-downloaders
;; agora deixamos o arquivo de configuracao vazio para que as alteracoes entre em processo

echo "" /etc/snmp/snmp.conf
agora 
snmpwalk -c public -v1 172.16.1.4


```

<mark style='background:var(--mk-color-red)'>Modificando dados via SNMP</mark> 

Como ja vimos , temos dois tipos de community , uma somente leitura , e uma de escrita.
Isso significa que podemos ler e escrever dados.

Outro comando para enumeracao
```sh
snmp-check <IP> -c public 
```

vamos supor que executamos o comando ``snmpwalker -c manager -v1 <IP>`` e ele nos retorna `sysContact.0` podemos alterar este dados com:

```sh
snmpset -c manager -v1 <IP> SNMPv2-MIB::sysContact.0 s "Desec"
SNMPv2-MIB::sysContact.0 = STRING: Desec
```

vamos confiramar isso com 
```sh
snmpwalk -c manager -v1 <IP> SNMPv2-MIB::sysContact.0
```

Lembrando que precisamos ter permissao 
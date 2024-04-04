```sh
ifconfig -> lista as redes disponiveis
ifconfig eth0 10.10.0.2 netmask 255.255.255.0 -> muda o IP e a Netmask
```

nano /etc/network/interfaces

auto eth0
iface eth0 inet static
address 192.168.0.200
netmask 255.255.255.0
gateway 192.168.0.1

service networking 
ou
/etc/init.d/networking restart
dhclient eth0

<mark style='background:var(--mk-color-purple)'>O Linux armazena a configuracao de gateway em uma rota e para ver isso basta digitar o comando :</mark>

```sh
❯ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    100    0        0 enp3s0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-fd5a6e9ec20d
172.19.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-78b20d3c5787
172.20.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-09405bf26fff
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
192.168.30.0    0.0.0.0         255.255.255.0   U     0      0        0 br10
```


<mark style='background:var(--mk-color-purple)'>O Gateway default  no nosso caso eh o roteador</mark> eh quem faz a rota para a internet
No caso para vermos o ip do roteador basta digitar

```sh
❯ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-fd5a6e9ec20d
172.19.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-78b20d3c5787
172.20.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-09405bf26fff
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
192.168.30.0    0.0.0.0         255.255.255.0   U     0      0        0 br10
```

<mark style='background:var(--mk-color-blue)'>PoC</mark>

Vamos fazer uma prova de conceito , vamos tentar acessar o site do google

```sh
❯ ping google.com
PING google.com (142.251.129.142) 56(84) bytes of data.
64 bytes from gru14s31-in-f14.1e100.net (142.251.129.142): icmp_seq=1 ttl=118 time=11.3 ms
64 bytes from gru14s31-in-f14.1e100.net (142.251.129.142): icmp_seq=2 ttl=118 time=11.5 ms
64 bytes from gru14s31-in-f14.1e100.net (142.251.129.142): icmp_seq=3 ttl=118 time=11.7 ms
```

Se deletarmos essa rota padrao do gateway ou seja do roteador iremos ficar sem internet

```sh
❯ route del default
172.18.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth0
```

Agora se tentarmos acessar o site do google novamente...

```sh
❯ ping google.com
connect: Network is unreachable
```

Para voltarmos a ter acesso a internet precisamos adicionar de volta essa rota

```sh
❯ route add default gw 172.18.0.1
❯ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.18.0.1      0.0.0.0         UG    0      0        0 eth0
```

Agora voltamos com a rota padrao do roteador e temos acesso novamente a internet

```sh
❯ ping google.com
PING google.com (142.251.129.142) 56(84) bytes of data.
64 bytes from gru14s31-in-f14.1e100.net (142.251.129.142): icmp_seq=1 ttl=118 time=11.3 ms
64 bytes from gru14s31-in-f14.1e100.net (142.251.129.142): icmp_seq=2 ttl=118 time=11.5 ms
64 bytes from gru14s31-in-f14.1e100.net (142.251.129.142): icmp_seq=3 ttl=118 time=11.7 ms
```
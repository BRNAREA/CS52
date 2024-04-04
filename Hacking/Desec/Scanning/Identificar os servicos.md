
```bash
nmap -v -sV -Pn 172.18.0.2
```

<h2 align="center">Servicos falsos</h2>
Podemos tambem confundir o invasor quando esta varrendo a rede, podemos entao
alterar diretamente o banner do servico com uma ferramenta hexeditor , assim voce confundira o atacante

<h2 align="center"> Identificando Sistema Operacional </h2>![[mpv-shot0007 1.jpg]]

```bash
nmap -v -O 172.18.0.2 -Pn
```

###### Alterar o TTL no Linux

```
nano /proc/sys/net/ipv4/ip_default_ttl
```

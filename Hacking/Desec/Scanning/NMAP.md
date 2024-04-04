Oque fazer entao quando o ICMP esta bloqueado , quando a gente ta no pentest externo  e precisa descobrir os hosts ativos? Existem outras tecnicas pra utilizar  pra identificar .. alem do ping , uma ferramenta interessante eh o NMAP.

O NMAP sem duvida eh o port scanner mais conhecido do mundo e a ferrramenta mais antiga e mais atualizada , entao sem duvidas eh uma das melhores ferramentas pra identificar a rede.

A opcao do nmap pra gente identificar host em uma rede seria o `nmap -sn` 

```sh
nmap -sn <IP>/<BARRAMENTO>
```

Agora pegamos esses hosts ativo e guardamos em um arquivo

```sh
nmap -sn <IP> -oG hostsativos
cat hostsativos | cut -d " " -f 2 > ips
```




<h2 align="center"> TCP HOST SCAN</h2>
A ideia aqui eh a gente identificar todas as portas abertas em um determinado host

O metodologia tcp host scan eh mais demorada porem mais eficiente e a mais recomendada ao realizar varreduras em hosts

```
nmap -v -sT -p- 192.168.1.2
```

<h2 align="center"> UDP HOST SCAN</h2>

Da mesma forma que a varredura em TCP , muitos servicos rodam em cima de UDP.

O problema do UDP eh que existe uma ambiguidade , segue abaixo

![[mpv-shot0006 1.jpg]]

```
nmap -v -sUV -p 161 172.18.0.2
```


<h2 align="center"> Encontrando vulnerabilidades com NMAP e NSE</h2>


```ad-tip
Por padrao os scripts do nmap ficam em <mark style='background:var(--mk-color-purple)'>/usr/share/nmap/scripts</mark>

Se voce esta procurando por algum script dentro do nmap basta pegar em script.db

<mark style='background:var(--mk-color-purple)'>cat /usr/share/nmap/scripts/script.db</mark>

Para usar argumentos de algum script , voce deve primeiro verificar o codig dele e o modo de uso mas basicamente ficaria algo como

nmap -p21 --script ftp-vsftpd-backdoor.nse <mark style='background:var(--mk-color-purple)'>--script-args cmd=pwd</mark> -Pn <IP>
```


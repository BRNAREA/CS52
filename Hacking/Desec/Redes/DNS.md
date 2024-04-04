
<h2 align="center">Domain Name System</h2>
<hr>

```ad-info
title: DNS
**Porta padrao: 53
Protocolo: UDP para consulta**
```

```ad-info
title: host
**-t=type (A,AAAA, MX, NS,CNAME, TXT)**

host -t txt terra.com.br (isso aqui pode revelar um pouco sobre blocos de ip que poderiamos estar mapeando e mostra como esta configurado o SPF)


Essa fase eh importante para comecarmos a mapear a superficie de ataque do ambiente e comecar a encontrar subdominios , possiveis servidores, enderecos ... Uma visibilidade sobre o ambiente.

Pra isso antes precisamos entender oque sao os registros DNS e oque faz cada um deles.
```


| Registros | Domain Name System    |
| --------- | --------------------- |
| **SOA**   | Registro Principal    |
| **A**     | Endereco IPv4         |
| **AAAA**  | Endereco IPv6         |
| **NS**    | Name Servers          |
| **CNAME** | Canonical Names       |
| **MX**    | Mail Exchange         |
| **PTR**   | Poiter (IP -> Nome)   |
| **HINFO** | Host Information      |
| **TXT**   | Text String (Ex: SPF) |


![[mpv-shot0002 2.jpg]]

Antes do DNS existir , para acessar algum site na internet teriamos que saber o endereco IP.

O DNS basicamente faz a traducao de nome para o endereco IP.

```ad-question
title: ROOT SERVER

Principais servidores que controlam a internet.
Quando o DNS nao sabe resolver o nome do IP eles vao perguntar para o Root Servers que vai conter aquele IP do nome especificado


```

![[mpv-shot0005 3.jpg]]



<h2 align="center"> Transferencia de zona</h2>
```ad-info
O alvo sempre tera no minimo 2 servidores para poder funcionar corretamente , isso se deve ao fato que se em caso do servidor 1 falhar o 2 entrara em acao, mas para isso o servidores devem estar 100% atualizados um com o outro .

O servidor primario mantem um registro com todas as entradas DNS como :CNAME , SUBDOMINIOS, Registros de IP etc.. entao sempre o servidor 1 respondera para nos.
```

```sh
host -t ns businesscorp.com.br
```

```ad-info
Se em caso o servidor 2 estiver desatualizado o servidor 1 vai forcar uma transferencia de zona para mantelo atualizado , para que nao haja erro em caso de algum desastre

A transferencia de zona funciona no protocolo DNS na porta 53 TCP
Enquanto as consultas DNS funcionam na porta 53 UDP
```

```sh
service rpcbind restart
service bind9 restart
rndc refresh businesscorp.com.br
zone refresh queued

tail -f /var/log/syslog | grep AXFR
```

Agora esta 100% atualizado.
Isso estamos falando na perspectiva da empresa.

```ad-bug
title: Zona de Transferencia
Se a gente encontrar a porta 53 TCP aberta em algum host do cliente que seja um servidor dns (ns) podemos tentar a transferencia de zona em todos os name servers naquele servidor se tivermos sorte , vamos conseguir ja ter direto todas as entradas DNS.

Se voce encontrar isso , vai abrir todo o mapa de onde estao cada servico, como firewall , sistema de monitoramento , enfim tudo isso via subdominio ali que conseguimos fazer a transferencia de zona
```

<h2 align="center"> Testando se o servidor deixa transferencia de zona</h2>

```
host -l -a  businesscorp.com.br ns2.businesscorp.com.br 
for server in $(host -t ns businesscorp.com.br | cut -d " " -f 4);do host -l -a businesscorp.com.br $server;done 

ou

dig -t ns  businesscrop.com.br +short
ns1.businesscorp.com.br.
ns2.businesscorp.com.br.

dig -t mx businesscorp.com.br +short
dig -t axfr businesscorp.com.br @ns1.businesscorp.com.br

ou

dnsenum --enum businesscorp.com.br
```

```ad-tip
title: Script basico para transferencia de zona
```

```sh
nano zonetransfer.sh
```

```sh
#!/bin/bash
for server in $(host -t ns $1 | cut -d " " -f 4);
do
host -l -a $1 $server
done
```

```sh
chmod +x zonetransfer.sh
./zonetransfer.sh
```

<h2 align="center"> Brute Force para DNS </h2>
<hr>

```sh
nano dnslookup.sh
```

```sh
#!/bin/bash
for palavra in $(cat wordlist.txt);do
host $palavra.$1 | grep -v "NXDOMAIN"
done
```

---

<h5 align="center"> Pesquisa reversa </h5>

```sh
nano dnsrev.sh
```

```sh
#!/bin/bash
for ip in $(seq 224 239);do
host -t ptr 37.59.174.$ip | grep -v "37-59-174" | cut -d " " -f 5
done
```

```sh
chmod +x dnsrev.sh
./dnsrev.sh
```


> [!tip] Ferramentas
> - dig -t ns businesscorp.com.br +short
> - dig -t axfr businesscorp.com.br @ns1.businesscorp.com.br  | transferencia de zona
> - dnsenum




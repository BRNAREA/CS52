<h2 align="center"> Escaneamento de portas </h2>
<hr>


Depois que a gente indentificou os hosts ativos na rede , o proximo passo eh identificar o mapeamento de portas  , porque se identificarmos as portas ativas no alvo , podemos identificar quais servicos estao rodando naquela porta para depois identificar a vulnerabilidade.

Antes de tudo para entendermos como funciona o escaneamento de porta , eh importante entendermos como funciona o [[3WHS - Three-way Handshake]] .

![[Servico Ativo.canvas]]


Entao quando um servico esta ativo  se voce enviou um `SYN` voce ja vai receber um `SYN/ACK` do servidor, e entao o servidor vai ficar aguardando voce enviar um `ACK` pra fechar o [[3WHS - Three-way Handshake]] e ai comecar a troca de dados.


E quando um servico esta inativo (PORTA 80 fechada) se enviarmos uma flag `SYN` ele nos retorna um `RST/ACK` indicando que o servico nao esta ativo

![[Servico Inativo.canvas]]


<h2 align="center"> Estudo tecnico</h2>
<hr>

A ideia eh entender oque acontece nos bastidores no mapeamento de portas , tanto aberta quanto fechada ou filtrada (firewall bloqueando aquela porta) de uma forma pratica 

Podemos utilizar entao o utilitario [[hping3]] para enviar pacotes personalizados da forma que a gente quiser .

```sh
hping3 -c 1 --syn -p 80 businesscorp.com.br
```

Vamos ver algo interessante , como as ferramentas conseguem identificar que o estado da porta eh filtrado ? `filtered` ? como a gente sabe que ha algum firewall la ?

Precisamos entender isso, se a gente fazer o mesmo processo com o `hping3` enviando um pacote `SYN` para o host e ele nao retornar nenhuma resposta , entao ele marca isso como `filtered` filtrado , isso eh um comportamento de firewall bloqueando (DROP) , dropando aquela conexao.

Entao sempre quando voce envia um pacote `SYN` e nao tem uma resposta, eh bem provavel que tenha um firewall , bloqueando aquela porta.

A gente pode tirar essas conclusoes usando o [[Wireshark]] e fazendo um scan `SYN` `nmap -sS` 
para um alvo com firewall em drop para aquele porta.

Um detalhe do [[Hacking/Desec/Scanning/NMAP]] eh que podemos colocar uma opcao `--reason` para vermos o motivo daquela porta nao nos dar uma resposta:

```sh
nmap -sS -p 80 -Pn 172.18.0.1 --reason

PORT   STATE    SERVICE REASON
80/tcp filtered  http   no-response #Firewall dropando a conexao

nmap -sS -p 23 -Pn 172.18.0.1 --reason
PORT   STATE SERVICE REASON
23/tcp open  telnet   syn-ack ttl 63 #Porta aberta , recebeu o syn-ack

nmap -sS -p 8055 -Pn 172.18.0.1 --reason
PORT   STATE   SERVICE   REASON
23/tcp closed  senomix   reset ttl 63 #Porta fechada, nao existe o servico ativo

```



```ad-important
title: ENGANANDO NMAP
iptables -A INPUT -p tcp --dport 80 -j REJECT --reject-with tcp-reset
```

```ad-note
title: RECAPTULANDO
PORTA ABERTA  | RESPONDE COM SYN\ACK(SA)
PORTA FECHADA | RESPONDE COM RST\ACK(RA)
PORTA COM FILTRO DE FIREWALL EM DROP | SEM RESPOSTA
PORTA COM FILTRO DE FIREWALL EM REJECT | RESPONDE COM ICMP PORT UNREACHEABLE
PORTA COM FILTRO DE FIREWALL  EM REJECT COM RST | RESPONDE COM PORTA FECHADA(RST)
```

<h1 align="center">Diferencas entre os tipos de scan</h1>

<h2 align="center">TCP Connect</h2>
<hr>

- [ ] Completa o [[3WHS - Three-way Handshake]]
- [ ] Facilmente detectavel e "barulhento"
- [ ] Consumo maior de trafego na rede
- [ ] Apos estabelecer o [[3WHS - Three-way Handshake]] envia um [[RST FLAG]] para encerrar a comunicacao.

```sh
nmap -sT -p 80 -Pn 172.18.1.5
```

<h2 align="center">Half Open/Syn Scan</h2>
<hr>

- [ ] Nao completa o three-way handshake
- [ ] Eh mais furtivo que o TCP Connect
- [ ] Consome menos trafego na rede

Ele inicia a comunicacao como se fosse estabelecer o three-way handshake mas ele para no meio do caminho , ou seja ele envia um `syn` se o host enviar um `syn/ack` ele ja envia uma flag `rst` , entao ele nao chega a fazer o 3whs

```sh
nmap -sS -p 80 -Pn 172.18.1.5
```
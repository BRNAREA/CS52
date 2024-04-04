```ad-tldr
title: **Post Office Protocol versão 3**
<mark style='background:var(--mk-color-purple)'>PORTA PADRAO DO POP3 110</mark>
Para a configuracao do servico dovecot que utiliza o protocolo pop3
temos que configurar a chave SSL na configuracao do dovecot , para gerarmos essa chave podemos fazer como nas aulas anteriores com o comando `openssl` AULA - [[NCAT com SSL]]
```

o POP3 é um protocolo que define como as mensagens de e-mail são retiradas de um servidor de e-mail. Protocolos garantem que os dispositivos envolvidos na comunicação entendam a forma como os dados são enviados, recebidos e interpretados.

Normalmente utilizada para uma caixa de entrada , inbox , correio eletronico email, quando
nos conectamos com esse servico conseguimos acessar essa caixa de entrada do cliente , daquele servidor de email.

Eh interessante a gente saber como que funciona isso , como interagimos com o protocolo , claro atraves da linha de comando , muita das vezes podemos com esse conhecimento encontrar essas vulnerabilidades , entao imagine que o servidor que voce esta realizando o pentest tem la a <mark style='background:var(--mk-color-purple)'>porta 110 </mark>com alguma vulnerabilidade , <mark style='background:var(--mk-color-purple)'>um bufferoverflow</mark> ou algo e na hora que interagimos com o servico eh que causa aquela vulnerabilide.

Um outro ponto eh que se voce sabe interagir com aquele servico , voce consegue obter mais informacoes  com os dados que voce vai coletando durante o pentest , tmb podemos encontrar exploits publicos na internet.

Entao no cenario abaixo vamos buscar a porta 110 nos hosts da rede

```bash
nmap --open -sS -p 110 -Pn  37.59.174.0/24

sudo nmap --open -sS -p 110 -Pn 37.59.174.0/24
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-03-26 19:10 UTC
Nmap scan report for ip28.ip-37-59-174.eu (37.59.174.28)
Host is up (0.23s latency).

PORT    STATE SERVICE
110/tcp open  pop3

Nmap scan report for ip29.ip-37-59-174.eu (37.59.174.29)
Host is up (0.23s latency).

PORT    STATE SERVICE
110/tcp open  pop3

Nmap scan report for ip30.ip-37-59-174.eu (37.59.174.30)
Host is up (0.24s latency).

PORT    STATE SERVICE
110/tcp open  pop3

Nmap scan report for ip31.ip-37-59-174.eu (37.59.174.31)
Host is up (0.23s latency).

PORT    STATE SERVICE
110/tcp open  pop3

Nmap scan report for ip74.ip-37-59-174.eu (37.59.174.74)
Host is up (0.23s latency).

PORT    STATE SERVICE
110/tcp open  pop3

Nmap scan report for ip75.ip-37-59-174.eu (37.59.174.75)
Host is up (0.23s latency).

PORT    STATE SERVICE
110/tcp open  pop3

Nmap scan report for ip76.ip-37-59-174.eu (37.59.174.76)
Host is up (0.23s latency).

PORT    STATE SERVICE
110/tcp open  pop3

Nmap scan report for ip77.ip-37-59-174.eu (37.59.174.77)
Host is up (0.23s latency).

PORT    STATE SERVICE
110/tcp open  pop3

Nmap scan report for ip78.ip-37-59-174.eu (37.59.174.78)
Host is up (0.23s latency).

PORT    STATE SERVICE
110/tcp open  pop3

Nmap scan report for ip79.ip-37-59-174.eu (37.59.174.79)
Host is up (0.23s latency).

PORT    STATE SERVICE
110/tcp open  pop3

Nmap scan report for ip227.ip-37-59-174.eu (37.59.174.227)
Host is up (0.22s latency).

PORT    STATE SERVICE
110/tcp open  pop3

```

Agora podemos pegar qualquer um dos host ativos que tem a porta 110 ativa e tentarmos nos conectarmos atraves do [[Hacking/Desec/Swiss Army Knife/Netcat]] ou [[Hacking/Desec/Swiss Army Knife/Telnet]]  

```bash
telnet 37.59.174.227 110         
Trying 37.59.174.227...
Connected to 37.59.174.227.
Escape character is '^]'.
+OK Hello there.

```

OK ! 😃 Sucesso conseguimos nos conectar , mas... e agora ?

Bom , lembra da coleta de informacoes que aprendemos nas aulas anteriores ? mais precisamente no Information Gathering Business ? -> [[Coletando e-mails]] , [[Leak data]] 

Seria uma boa hora para utilizarmos . Entao vamos la

```bash
telnet 37.59.174.227 110         
Trying 37.59.174.227...
Connected to 37.59.174.227.
Escape character is '^]'.
+OK Hello there.
USER camila
+OK Password required.
PASS ca123456 
+OK logged in.

```

Conseguimos ! 😀 estamos logado no usuario da camila que teve suas informacoes vazadas na coleta de informacoes.

Depois que a gente loga  , poderiamos utilizar  o comando ``STAT`` para ele mostrar o status 

```bash
STAT
+OK 0 0 -> 0 Mensagens
```

O comando ``LIST`` para listar  essas mensagens

```bash
LIST
+OK POP3 clients that break here, they violate STD53.
No caso temos 0 mensagens entao nao aparece nada mas se tivesse.. poderiamos
```

Poderiamos ver as mensagens com ``RETR 1`` para ver a primeira mensagem

```bash
RETR
```
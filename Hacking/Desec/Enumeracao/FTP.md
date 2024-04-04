<h2 align="center"> File Transfer Protocol</h2>

```ad-tip
PORTA PADRAO DO FTP : 21
```

A melhor forma de se enumerar o protocolo FTP eh se conectando diretamente a eles e pegando o banner.

Ferramentas e utilitarios:

```bash

nmap -v -sV -p21,2121 -Pn --open 172.18.0.0/24 -oG ftp

nc -vn 172.16.1.108 21
((UNKNOW)) [172.16.1.254] 2121 (iprop) open
220 (vsFTPd 3.0.3)

nc -vn 172.16.1.245 2121
((UNKNOW)) [172.16.1.108] 21 (ftp) open
220 (Microsoft FTP Service)

```

Legal, a gente ja viu essa primeira parte , o que precisamos saber agora eh como trabalhamos com o protocolo FTP , precisamos entender o protocolo para sabermos interagir com ele.

Entao por exemplo suponhamos que a gente pegue o ip 172.16.1.108 na porta 21 (ftp)
Vamos nos conectar a ele

```bash
nc -vn 172.16.1.108 21

ele nos traz o banner
(UNKNOWN) [192.168.1.6] 21 (ftp) open
220 archx64 FTP server (GNU inetutils 2.5) ready.
```

E agora oque fazemos? ele esta aguardando algum comando ue, simples..
Entao vamos enviar o comando USER para nos autenticarmos e tantarmos algo.

```bash
nc -vn 172.16.1.108 21

ele nos traz o banner
(UNKNOWN) [192.168.1.6] 21 (ftp) open
220 archx64 FTP server (GNU inetutils 2.5) ready.
USER wallace

331 Password required for wallace.
# Aqui ele pede a senha entao enviamos o comando [PASS]
PASS senhaforte123

530 Login incorrect.
Se o login estiver incorreto nao teremos acesso entao basta dar o comando QUIT
QUIT
221 goodbye !

entao saimos do ftp


```

Podemos tmb usar simplesmente o ftp command dai nem precisamos especificar a porta.

```bash
ftp 192.168.1.6   
Connected to 192.168.1.6.
220 archx64 FTP server (GNU inetutils 2.5) ready.
Name (192.168.1.6:root): admin
331 Password required for admin.
Password: 
530 Login incorrect.
ftp: Login failed

```

Ok aprendemos a enumerar o ftp e a como lidar com ele, agora vamos falar de um processo de enumeracao comum para ftp que seria o ftp anonimo.

Muita das vezes o servidor ftp esta configurado com um usuario anonymous ou ftp e a senha tmb vai ser anonymous ou ftp

<h3 align="center"> FTP com Python</h3>


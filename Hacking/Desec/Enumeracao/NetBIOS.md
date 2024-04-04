
<h2 align="center"> NETBIOS E SMB </h2>

```ad-info
PORTA PADRAO DO NETBIOS 139 (TCP)
PORTA PADRAO SMB 445 (TCP)
```

Sao responsaveis por compartilhamento de arquivos e diretorios entao quando  voce ta numa rede onde voce tem o mapeamento dela quando voce conecta voce puxa arquivos do servidor envia arquivos.. ou  entao quando voce ta numa rede e quer compartilhar arquivos da sua maquina outra pessoa pode acessar ela e dps vc acessa de outra pessoa , enfim voce provavelmente esta usando o protocolo NETBIOS ou SMB.

![[mpv-shot0002 6.jpg]]

```ad-info
NetBIOS eh mais antigo - Antigamente nao existia suporte a TCP/IP para NetBIOS
Depois veio o NBT com suporte a TCP
Depois veio o SMB - Que ja eh para sistemas mais mordenos

Porta 139 - Sistemas antigos
Porta 445 - Sistemas recentes
```


```ad-hint
title: Null Session
Estabelece uma conexao sem precisar de credenciais de autenticacao somente com os campos em brancos " "
```

IPC$ - Compartilhamento administrativo , nao so no windows como no samba, ele serve para compartilhamento de comunicacao entre processos dos hosts que estao se comunicando na rede.

<h3 align="center">Brute force SMB/NetBIOS no prompt do Windows</h3>
### Windows

```powershell
for /f %i in (senhas.txt) do net use \\<IP.ADDRES> %i /u:$USER

ou

for /f "tokens=1,2" %i in (credenciais.txt) do net use \\<IP.ADDRES> %j /u: %i

```
<h3 align="center">Brute force SMB/NetBIOS no prompt do Linux</h3>
### Linux
Uma vez que escaneamos a rede com as portas 139 e 445 e identificou quais hosts  possui essas portas ativas a gente pode comecar a fazer a enumeracao desses hosts  e dos protocolos

no linux podemos utilizar o `nbtscan -r 172.16.1.0/24`


```bash
nmap -v -sV -p139,445 -Pn --open 172.18.0.0/24

nbtscan -r 172.18.0.0/34 ; vai escanear toda essa rede pro protocolo netbios

IP address   NetBIOS name  Server  User  MAC address
-----------------------------------------------------
172.16.1.5     SERVER5     <server>  SERVER5 00:00:00:00:00:00
172.16.1.6     WKS01       <server> <UNKNOW> 00:00:00:00:00:00
172.16.1.8     SRVINT      <server> <UNKNOW> 00:00:00:00:00:00
172.16.1.10    SMB         <server>   SMB    00:00:00:00:00:00
172.16.1.16    SRVCODE     <server> <UNKNOW> 00:00:00:00:00:00
172.16.1.243   USUARIO-PC  <server> <UNKNOW> 00:00:00:00:00:00
172.16.1.244   LAB023      <server> <UNKNOW> 00:00:00:00:00:00

```

Para termos algum comando e enumerarmos igual fizemos com o windows como o `net use & net view` a gente pode utulizar o smbclient --help

```bash
smbclient -L -N \\172.16.1.5 ; (-N para null session)

;; Se ja soubermos que ha diretorios podemos tentar entrar no mesmo.
smbclient //172.16.1.5/_DOCS -N
;; aqui nos conectamos com o diretorio.
```


Em alguns casos , pode acontecer da conexao ser recusada , isso se deve ao fato de que a versao do smbclient pode estar desatualizada , para isso bastar pastar o parametro options especificando a versao

```bash
-smbclient -L \\37.59.174.73 -N --option='client min protocol=NT1'
```


<h2 align="center">RPCLIENT</h2>
Um utilitario bacana eh o rpclient no qual quando conseguimos conectar no host utilizando ele podemos obter varias informacoes interessantes como : usuarios, info sobre hosts e etc..

```ad-tldr
title: RPCLIENT

PORTA PADRAO DO RPC 139 OU 445 (TCP) NETBIOS OU SMB
RPC = Chamada de procedimento remoto
Ferramenta para ver funcoes no MS-RPC
Uma API basicamente
Podemos utilizar para conseguir executar comandos quando estabelecemos uma conexao com o host.

```




```bash
rpcclient -U "" -N 172.16.1.5
rpclient $> enumdomusers
rpcclient $> queryuser root
```


<h2 align="center">ENUM4LINUX </h2>

```bash
enum4linux -U 192.168.1.6

Starting enum4linux v0.9.1 (http://labs.portcullis.co.uk/application/enum4linux/ ) on Tue Mar 26 17:48:41 2024

 =========================================
 (Target Information)
 =========================================

Target ........... 192.168.1.6
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none


 ============================
 ( Enumerating Workgroup/Domain on 192.168.1.6 )
 ============================

[+] Got domain/workgroup name: SPEC

 ====================================
 ( Session Check on 192.168.1.6 )
 ====================================
 
[+] Server 192.168.1.6 allows sessions using username '', password ''                 
 =================================
 ( Getting domain SID for 192.168.1.6 )
 =================================                                                                   
Domain Name: SPEC                                                                     
Domain Sid: S-1-5-21-1710571472-3779224585-1708222386

[+] Host is part of a domain (not a workgroup)                                        
 ========================================
 ( Users on 192.168.1.6 )
 ========================================                                                                   
index: 0x1 RID: 0x1f5 acb: 0x00000000 Account: Guest    Name:   Desc: Built-in account for guest access to the computer/domain
index: 0x2 RID: 0x1f4 acb: 0x00000000 Account: Administrator    Name:   Desc: Built-in account for administering the computer/domain
index: 0x3 RID: 0x1f6 acb: 0x00000000 Account: krbtgt   Name:   Desc: Key Distribution Center Service Account

user:[Administrator] rid:[0x1f4]
user:[Guest] rid:[0x1f5]
user:[krbtgt] rid:[0x1f6]
enum4linux complete on Tue Mar 26 17:48:41 2024


OU


enum4linux -a <IPADRRES>
```

<h2 align="center">NMAP PARA NETBIOS E SMB</h2>

Eh interessante para nos usarmos o nmap neste caso de netbios e smb nao somente para detectarmos vulnerabilidades mas tambem para obter mais informacoes do ambiente

```ad-info
DIRETORIO NMAP PARA SMB
ls /usr/share/nmap/scripts/smb

```

Aqui ha varios scripts para identificacao de enumeracao , vulnerabilidades ja encontradas e alguns outro entao podemos fazer

```bash

nmap -v  --script=<NOMEDOSCRIPT> <HOST>
nmap -v --script=smb-os-discovery 192.168.1.6

Se quisermos utilizar para ja acharmos alguma vulnerabilidade podemos passar o coringa para pesquisar por todas vulnerabilidades ja conhecidas ex:

nmap -v --script=smb-vuln* 192.168.1.6
```

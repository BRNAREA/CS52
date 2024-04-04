<h2 align="center"> Trabalhando com a base de dados</h2>
<hr>


Se voce tiver utilizado o nmap no metasploit e quiser ver quais foram os hosts e as portas escaneadas :
```
services
services -p 21
```

Vamos ver como fazer um escaneamento um pouco mais eficiente sem o modo auxiliar e armazenando tudo na base de dados:

```sh
db_nmap -v --open -sV -Pn <IP>
```

Podemos tambem usar o nmap da forma convencional e depois importarmos para o metasploit
```sh
nmap -v --open -sV -Pn <IP> -oX /opt/host4.xml
```

Ele vai escaneer e jogar para um xml e jogar pra `/opt/`

E no metasploit 

```sh
db_import /opt/host4.xml
services
```


Agora para mostrar todos os hosts:

```
hosts
```

Agora para tentar buscar por vulnerabilidades nesses hosts:

```sh
Vulns
```


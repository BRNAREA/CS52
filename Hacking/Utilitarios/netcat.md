```ad-info
- -v=verbose
- -n=no-resolve-host
- -l=listen
- -zp=port
- -z=scanning

```


```sh
nc -vnlp 80 < index.html
nc -vn 443
```

<h2 align="center">UDP e Transferencia de arquivos</h2>
<hr>

Com o netcat tmb conseguimos transferir arquivos e fazer conexoes UDP

```sh
nc -vnlup 53
```

na outr maquina

```sh
nc -vnu <IP> 53
```

transferindo arquivos:

na outra maquina que vai receber o arquivo:
```sh
nc -vnlp 5050 > ncat.exe
```

na maquina que vai enviar o arquivo: 
```sh
nc -v <IP> 5050 < ncat.exe
```

<h2 align="center">Port Scanning com NCAT</h2>
<hr>

```sh
nc -vnz <IP> <PORT>
nc -vnz <IP> 20-25
```


<h2 align="center">Honey Pot </h2>
<hr>

```sh
while true;do nc -vnlp 21 < 21.txt >> 21.log 2>> 21.log;echo $(date) >> 21.log;done
```


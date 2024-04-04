<h1 align="center"> Bypass IPS IDS FW  - Portsentry , Snort , IPTables</h1>

<hr>


Do lado do atacante a primeira coisa que a gente tem que fazer eh pensar em ser o mais furtivo possivel , mas podemos comecar fazendo uma varredura com `SYN SCAN` e ao inves de varrer todas as portas , a gente vai varrer portas especificas , mais faceis de encontrar no ambiente , ou `top-ports` no scaneamento inicial , tambem podemos colocar so pra ele nos trazer portas abertas , e tambem tem como mexer na questao do tempo `-T 2`, quanto mais rapido mais barulhento por isso recomendamos deixar no -T 2

Outra opcao que vai nos ajudar muito na hora de ser furtivo seria a opcao `-D` ou `decoy`
esta opcao vai colocar um monte de hosts fantasma para confundir o IPS  e o IDS do alvo

```sh
nmap -v -D RND:20 -sS --top-ports=25 --open -Pn 192.168.0.11
```

![[mpv-shot0002 5.jpg]]


```sh
nmap -v -D RND:20 -sV --top-ports=10 --open -g 80 -T 2 -Pn -iL hosts --reason

nmap -v -D RND:20 -sUV --top-ports=10 --open -g 53 -T 2 -Pn -iL hosts --reason
```

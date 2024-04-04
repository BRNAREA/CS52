<h1 align="center">CAPTURA  DE HASHES E CREDENCIAIS NA REDE NBT-NS / LLMNR & MDNS </h1>
<hr>

Antes de irmos a pratica vamos explicar como ocorre todo esse proceso aqui.

```ad-question
title: Como funciona?

NBT-NS - NetBIOS Name Service
LLMNR - Link-Local Multicast Name Resolution
mDNS - Multicast Domain Name System
```

Pra gente entender isso vamos partir que a gente tem um determinado host em nossa rede que ele vai tentar se comunicar com outro host (um servidor por exemplo) , entao como esse host quer tentar se comunicar com o seridor01 ele vai primeiro tentar resolver isso com o DNS , se o DNS souber beleza ele vai retornar e tudo ok, se o DNS nao souber , esse mesmo host vai enviar um broadcast pra toda rede , ele vai fazer isso atraves de um dos tres protocolos da imagem (NBT-NS, LLMNR, mDNS), ele vai utilizar alguim deles para fazer um broadcast na rede perguntando quem eh o servidor01.

Entao como funciona o ataque ?

Depois de fazer a requisicao broadcast , nos (o atacante) vamos ficar escutando na rede por requisicoes NBT-NS , LLMNR e mDNS, quando vir algum broadcast pra rede com algum tipo dessas requisicoes ele vai responder como sendo aquilo que foi pesquisado no nosso caso , o servidor01 dai entregamos nosso endereco IP onde temos um rog (servico falso) na qual vai tentar estabelecer a comunicacao , ao fazer isso o host que perguntou enviara os hashes e fazendo isso o atacante finaliza a comunicacao.
![[mpv-shot0002 12.jpg]]
```sh
responder -I enp3s0 -Prv
```

```ad-faq
-P=ProxyAuth | Forca uma autenticacao transparente (usuario nao ve nada)
-r | Habilitar resposta de NetBIOS
-v | Verbose
```

- hashid
- hashcat

```sh
hashcat -m 5600 hashes /usr/share/wordlists/rockyou.txt --force
```

```sh
john --format=netntlmv2 hashes --wordlist=/usr/share/wordlists/rockyou.txt
```

Essa ferramenta tem outros recursos onde voce pode habilitar pra ele servir um executavel e ai quando o usuario tentar baixar o executavel ele troque esse executavel e se infecte.
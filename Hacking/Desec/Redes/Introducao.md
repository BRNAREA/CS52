
<h1 align="center">Redes de computadores</h1>
<hr>

<mark style='background:var(--mk-color-blue)'>Comunicacao entre dois ou mais computadores</mark>

<mark style='background:var(--mk-color-purple)'>
Host - Nome atribuido a um computador na rede</mark>

<mark style='background:var(--mk-color-blue)'>Servidor - Fornece algum servico a rede</mark>

<mark style='background:var(--mk-color-purple)'>Cliente - Consome algum servico oferecido por um servidor</mark>

Oque diferencia de um host cliente pra um host servidor eh se ele esta consumindo servico ou fornecendo servico.
<h1 align="center">Protocolos</h1>
<hr>

Garantem  que diferentes computadores usando diferentes harwadres e softwares consigam  se comunicar.

Um **protocolo** eh um conjunto de regras e procedimentos para transmitir dados entre dispositivos na rede

Exemplo de protocolos de rede: TCP/IP

A comunicacao so ocorre pois existe um protocolo, no qual, ambos os lados compreendem

<h1 align="center">Servicos</h1>
<hr>

Um **serviço** refere-se a um programa ou aplicacao que executa uma tarefa especifica em um sistema , geralmente aguardando por solicitacoes atraves da rede. Por exemplo , um servidor de email pode oferecer servicos de email que utilizam protocolos como IMAP ou POP3 para permitir que clientes de email acssem e gerenciem suas mensagens.


<h1 align="center">Enderecos Fisicos e Logicos e Portas</h1>

<hr>

 Enderecos fisico eh conhecido como MAC Address e vem definido de fabrica.

Endereco logico eh atribuido ao adaptador de rede de acordo com a rede.

Cada servico ativo usa uma porta de identificacao

<h1 align="center">Endereco Fisico (MAC Address)</h1>
<hr>

Formado por uma sequencia de 6 bytes

**A4:5E:60:B8:C1:AF**

Os tres primeiros bytes indicam o fabricante
Os tres ultimos bytes eh uma sequencia unica gerado pelo fabricante

Para descobrir o fabricante:

http://standards-oui.ieee.org/oui/oui.txt
https://macvendors.com/

<h1 align="center">Endereco Logico (IP Address)</h1>
<hr>

O Endereco IP eh formado por 4 octetos representados de forma decimal.

Existem varias classificacoes de endereco IP e cada uma serve para definir o uso em uma rede de acordo com a necessidade.

<mark style='background:var(--mk-color-purple)'>
Mascara de rede</mark>:

<mark style='background:var(--mk-color-purple)'>Ex: 255.255.255.0</mark>

<mark style='background:var(--mk-color-charcoal)'>192.168.0.200</mark>
<mark style='background:var(--mk-color-purple)'>os tres primeiros octetos definem a rede e o ultimo o host</mark>

<h1 align="center">Roteamento</h1>
<hr>

Redes diferentes so se enxergam atraves do roteamento de rede, para isso precisam definir um gateway.

Porque conseguimos acessar o google por exemplo?
Porque o nosso Gateway faz o nosso roteamento... ele pega o nosso pacote da nossa rede interna e leva pra internet

Sem o Gateway a gente nao consegue acessar a internet.

```sh
route -n ;; Ver endereco roteador

route del default gw <ENDERECO DO ROTEADOR> ;; deletamos nosso gateway se tentarmos acessar a internet agora , nao vamos conseguir.

route add default gw <ENDERECO DO ROTEADOR> ;; adicionamos de volta nosso gateway , agora conseguimos nos conectar a internet

```

Se voce quiser ver os detalhes sobre as classes de IP's , podemos usar o comando `ipcalc`

```sh
ipcalc <IP>/<NETMASK>
```

<h1 align="center">Portas</h1>
<hr>

Uma **porta** é um identificador numérico utilizado em redes de computadores para especificar um ponto final de comunicação específico em um host. Em termos de internet e redes TCP/IP, uma porta serve para direcionar os pacotes de dados para a aplicação ou serviço correto. Cada serviço que ouve na rede geralmente é associado a uma porta específica; por exemplo, o POP3 geralmente usa a porta 110 (ou 995 para conexões seguras, POP3S).

Um servico pode ser configurado para funcionar em outra porta que nao seja a padrao.

Exemplos:

Um servidor SSH pode ser configurado para rodar na porta 2222 ao inves da porta 22

```ad-example
title: <mark style='background:var(--mk-color-purple)'>SOCKET</mark>

Socket eh quando temos o conjunto de IP + Porta, quando juntamos os dois ele forma um socket.

<mark style='background:var(--mk-color-purple)'>IP:PORTA</mark>
EX: 192.168.0.1:8080

```


<h2 align="center"> </h2>

<h2>Mudando Endereco Mac</h2>

```sh
yay -S macchanger
sudo macchanger -r enp3s0  ;; Troca o endereco mac
sudo macchanger -p enp3s0  ;; Volta o endereco mac trocado anteriormente
sudo macchanger -m 00:11:22:33:44:55 enp3s0  ;; Definir um endereco mac manualmente

Modo de uso: macchanger -r <REDE>
```


<h2>Calculando a rede</h2>

```sh
yay -S ipcalc
ipcalc 192.168.1.6/255.255.255.0
Address:   192.168.1.6          11000000.10101000.00000001. 00000110
Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
=>
Network:   192.168.1.0/24       11000000.10101000.00000001. 00000000
HostMin:   192.168.1.1          11000000.10101000.00000001. 00000001
HostMax:   192.168.1.254        11000000.10101000.00000001. 11111110
Broadcast: 192.168.1.255        11000000.10101000.00000001. 11111111
Hosts/Net: 254                   Class C, Private Internet
```
### Diferenças e Relações

- **Protocolo vs. Serviço:** Um protocolo é como a "linguagem" usada para a comunicação, enquanto um serviço é uma aplicação que realiza ações específicas, como enviar um e-mail ou hospedar um site. Um serviço pode utilizar um ou mais protocolos para comunicar-se pela rede.
    
- **Serviço vs. Porta:** Um serviço "escuta" em uma porta específica em um dispositivo para receber comunicações da rede. A porta é essencialmente a "porta de entrada" para aquele serviço específico, permitindo que ele seja acessado remotamente.
    
- **Protocolo vs. Porta:** O protocolo define como a comunicação deve ocorrer, enquanto a porta é apenas um aspecto técnico que permite que múltiplos serviços operem em um único dispositivo, direcionando o tráfego apropriadamente.
    

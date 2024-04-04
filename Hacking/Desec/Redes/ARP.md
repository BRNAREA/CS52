<h2 align="center">Protocolo ARP</h2>

O ARP tem habilidade de descobrir qual endereco MAC esta associado a um determinado endereco IP para todos os enderecos na rede ou seja BROADCAST.

Para fazer isso o ARP utiliza os famosos <mark style='background:var(--mk-color-purple)'>ARP Request e ARP Reply</mark>

<mark style='background:var(--mk-color-purple)'>ARP Request</mark> pergunta quem tem um determinado IP e qual o seu endereco MAC.

<mark style='background:var(--mk-color-purple)'>ARP Reply </mark>eh a resposta enviada pelo host que tem o IP requisitado, ao responder ao ARP o host envia seu endereco MAC.

O host que recebe a resposta armazena o IP e MAC por um tempo.

```ad-tldr
Lembrando que o protocolo ARP faz a requisicao para o [[Ethernet]]
```

Entao ele basicamente pergunta para todos na rede quem tem o determinado endereco MAC para todos os enderecos IP's na rede , ele faz isso atraves do <mark style='background:var(--mk-color-purple)'>ARP Request</mark>

E entao o host de resposta envia o seu endereco MAC.


<h2 align="center">Importancia do ARP </h2>
<hr>


```sh
arp -an ;; usado para ver a tabela arp
```

Vamos supor que temos um servidor web em nossa maquina, e uma outra pessoa queira acessar esse servidor , o que sera feito e uma requisicao arp.

se em nossa maquina nao tiver o endereco MAC daquela outra pessoa , um ARP request eh disparado para toda rede perguntando quem tem o aquele IP , e entao aquele IP envia um ARP Reply devolvendo seu endereco MAC. Entao quando chega ate o nosso servidor , ele atualiza a sua tabela arp.

<h1 align="center"> Estrutura do protocolo ARP</h1>


![[Screenshot 2024-03-20 17-13-37.png]]



```ad-important
title: Estrutura do ARP

<mark style='background:var(--mk-color-red)'>A estrutura do protocolo ARP tem 4 bytes de largura</mark> isso eh MUITO IMPORTANTE porque <mark style='background:var(--mk-color-red)'>o endereco MAC ele usa 6 bytes</mark> e <mark style='background:var(--mk-color-red)'>o endereco IP usa 4 bytes</mark>, se a estrutura como um todo do ARP possui 4 bytes de largura , significa que alguns campos ali nao vao caber o endereco mac inteiro, entao muita das vezes voce ira ver uma estrutura do protocolo arp simplificada
```


![[Screenshot 2024-03-20 17-15-27.png]]

Podemos ver na linha verde escuro em `Sender hardware address (MAC de origem)` 
Veja que nessa ele so ira usar os 4 bytes do MAC + 2 bytes na linha de baixo , para que se encaixe todo o endereco. Como o MAC ocupa 6 bytes ele faz com que os outros enderecos usem os enderecos adjacentes.

Para mais facilidade da imagem acima veja como ficaria conforme o explicado .

![[Screenshot 2024-03-20 17-19-19.png]]

```ad-question
Sabemos que isso funciona localmente , mas e quando eu to fazendo uma conexao internet eu vou ter o MAC das maquinas que eu comunico na internet?

R: Nao , a tabela arp so funciona na rede local

Basicamente o endereco MAC que temos eh do nosso roteador e nao da maquina em si, isso porque quem faz o roteamento de pacotes eh o roteador e nao a maquina.
```

<h2 align="center"> Bytes na rede</h2>
<hr>

Nos vimos frames, pacotes, segmentos e payloads mas isso eh oque nos enxergamos, isso tudo eh formado por bytes trafegados na rede.

### Analisando Bytes - Linha 1

Os primeiros 6 bytes sao o MAC de destino, logo em seguida temos o MAC de origem e nos proxmimos 2 bytes temos o protocolo que no caso de 08 00 indica protocolo IP .

<mark style='background:var(--mk-color-green)'>d4 ab 82 45 c4 0c </mark><mark style='background:var(--mk-color-turquoise)'>00 0c 29 76 43 e1</mark> <mark style='background:var(--mk-color-purple)'>08 00 </mark>45 00

Depois dos bytes que indicam o protocolo vem os bytes de cabecalho e payload do mesmo

<mark style='background:var(--mk-color-green)'>d4 ab 82 45 c4 0c </mark><mark style='background:var(--mk-color-turquoise)'>00 0c 29 76 43 e1</mark><mark style='background:var(--mk-color-purple)'>08 00 </mark><mark style='background:var(--mk-color-orange)'>4</mark><mark style='background:var(--mk-color-blue)'>5</mark><mark style='background:var(--mk-color-yellow)'>00</mark>
<mark style='background:var(--mk-color-red)'>01 81</mark>
![[mpv-shot0009.jpg]]

### Analisando Bytes - TCP

![[mpv-shot0010.jpg]]

![[mpv-shot0011.jpg]]

![[mpv-shot0012.jpg]]

![[mpv-shot0013.jpg]]

### Analisando o Payload

![[mpv-shot0015.jpg]]


![[mpv-shot0014.jpg]]

![[mpv-shot0016.jpg]]

Um detalhe importante.
Como se trata de uma comunicacao  que ta saindo da nossa rede local e indo pra internet em direcao a algum servidor o MAC  de destino NAO sera o MAC do servidor e sim o MAC do nosso ROTEADOR 
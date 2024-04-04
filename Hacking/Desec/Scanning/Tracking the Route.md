<h1 align="center">Rastreamentpo de rotas </h1>
<hr>

- Indentificar a rota que os pacotes fazem ate chegar no alvo
- Identificar possiveis filtros e bloqueios
- Identificar quais pacotes sao aceitos

O host aceita UDP ? TCP ? ICMP ? 
O host aceita permite determinadas portas ?

## Como funciona?

Quando o TTL se torna 0 normalmente o roteador utiliza o protocolo ICMP para avisar, entao ele utiliza o ICMP de tipo 11 e codigo 0.

Sendo assim, podemos manipular o TTL afim de descobrir o caminho e a rota que o pacote percorre.


![[mpv-shot0001 4.jpg]]


Quando usamos o ``traceroute`` por padrao leva 3 segundos para o roteador responser

caso este tempo seja excedido ele colocara um * que significa que nao houve uma resposta nesse intervalo de tempo

Quando vemos * * * (tres astericos) significa
que provavelmente aquele roteador nao aceita o protocolo que foi enviado , que no caso do traceroute seria UDP
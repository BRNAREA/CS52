<h2 align="center"> Protocolo Ethernet</h2>
<hr>

<mark style='background:var(--mk-color-purple)'>O protocolo Ethernet ele entende enderecos fisicos apenas</mark> , entao oque ele vai carregar de informacao no header dele sao os enderecos fisicos (MAC Address)

Estrutura do protocolo ethernet:

| <mark style='background:var(--mk-color-orange)'>Mac de destino</mark> | <mark style='background:var(--mk-color-yellow)'>Mac de Origem</mark> | <mark style='background:var(--mk-color-green)'>Tipo</mark> | <mark style='background:var(--mk-color-turquoise)'>Payload</mark> | <mark style='background:var(--mk-color-teal)'>Checksum</mark> |


Mac Destino: Contem o endereco fisico da placa de rede de destino

Mac de Origem: Contem o endereco fisico da placa de rede de origem

Tipo: Codigo que identifica o tipo de protocolo | (0800 = IP / 0806 = ARP)

Payload: Contem os dados a serem transportados (outros protocolos) , o tamanho maximo do payload ethernet e de  1500 bytes.


```ad-info
title: Frame Ethernet e Fragmentacao de Pacotes
Um frame ethernet aceita por padrao no maximo 1500 bytes, sendo assim, se o pacotes IP tiver mais de 1500 bytes ele devera ser dividido em diversos pedacos, o que chamamos de fragmentacao de pacotes.

Exemplo: O host cliente envia um ping para o host servidor com um pacote com 4000 bytes de tamanho
```

```sh
ping -c 1 -s 4000 192.168.0.1
```

## Exemplos praticos

```ad-note
title: Oque e Broadcast?
Broadcast eh o endereco que indica todo o segmento ethenet  ou seja todo mundo na rede.
Ele tambem eh sempre o ultimo endereco da rede , sendo por exemplo um IP de Classe C 192.168.0.255
__(ff:ff:ff:ff:ff:ff)__
```



![[mpv-shot0003 4.jpg]]
No caso acima:
O Destino eh o broadcast.
O Source (Origem) eh o endereco MAC da maquina que esta enviando a mensagem.
No Type: os bytes (0x0806) indica que o protocolo que ele vai carregar eh o ARP.


![[mpv-shot0004 4.jpg]]
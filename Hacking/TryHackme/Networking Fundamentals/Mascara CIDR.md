<h1 align="center"> Classless Inter-domain Routing </h1>
Uma máscara CIDR (Classless Inter-Domain Routing) é uma notação utilizada para designar a porção de rede e a porção de host em um endereço IP. Ela é usada para dividir uma rede em sub-redes menores, permitindo uma alocação eficiente de endereços IP.

O princípio básico da máscara CIDR é o uso da notação de barra (/) seguida de um número para indicar o tamanho da rede. Essa notação especifica quantos bits no endereço IP representam a rede e quantos bits representam o host.

Por exemplo, se um endereço IP é representado como 192.168.0.0/24, isso significa que os primeiros 24 bits (ou os primeiros três octetos) são a parte da rede, enquanto os últimos 8 bits (ou o último octeto) são a parte do host. O número após a barra (/) indica o número de bits na máscara de rede.

Ao usar máscaras CIDR, é possível criar sub-redes mais eficientes, pois você pode ajustar o tamanho da rede conforme necessário, alocando a quantidade apropriada de endereços para cada sub-rede. Isso permite um melhor aproveitamento dos endereços IP disponíveis e ajuda a controlar o tráfego de rede de forma mais eficiente.

Em resumo, uma máscara CIDR é usada para definir o tamanho da rede e da parte do host em um endereço IP, permitindo a divisão eficiente de uma rede em sub-redes menores. Isso é fundamental para otimizar o uso dos endereços IP e facilitar o gerenciamento de redes.

![[Mascara CIDR 2023-06-12 14.11.16.excalidraw]]

```ad-note
title: Unicos enderecos possiveis em mascaras CIDR

255
254
252
248
240
224
192
128
0
```
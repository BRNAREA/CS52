
<h2 align="center">Liberando Portas no Roteador</h2>
<hr>

```ad-question
title: Oque eu Port Forwarding?

```


![[mpv-shot0001 10.jpg]]

Suponhamos que temos a nossa maquina atacante em uma rede local com o endereco 192.168.0.200 com a porta 8443 aberta

Pra essa rede acessar a internet  utiliza um roteador esse roteador se conecta ao provedor e o provedor fornece um IP publico para a maquina poder acessar a internet

Este endereco publico poed ser dinamico ou pode ser um IP fixo.

Imagina que precisamos abrir uma porta na nossa maquina , se simplesmente nos abrirmos a porta 8443 ou subir um servico nesta porta e as outras pessoas tentarem acessar ou tentar acessar a partir da internet usando o nosso IP publico eh bem provavel  que elas nao vao conseguir acessar esse servico .

Isso porque nao fizemos o encaminhamento de portas  no roteador.

Entao o Port Forwarding ele serve justamente para que quando um pacote chega no roteador , o roteador saiba direcionar o pacote para o IP correto , para o IP que tenha aquela porta aberta.
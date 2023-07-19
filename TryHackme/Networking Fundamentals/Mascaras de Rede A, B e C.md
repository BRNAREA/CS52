A Mascara de Rede vai dizer ao computador , equipamentos de rede  etc .. Qual eh o padrao de identificacao que ele tem que utilizar.

O Computador entende somente binario entao ele nao tem capacidade de dizer que o endereco 192.168.0.1 seria de Classe C , quem faz isso eh a **Mascara de Rede**. Mas dai surge a duvida : "AH Mais meu computador ja preenche automaticamente minha Mascara de Rede..." , bom  na verdade quem faz isso seria o *Sistema Opercional* e nao a maquina quem em si..

Para saber a mascara de Rede voce precisa saber de duas coisas :

- A Classe da Rede
- Identificacao de Rede e Host

# Colocando Mascara de Rede

As Mascaras de Redes sao um padrao , como dito a cima voce precisa saber a classe e identificar a rede e o host. 

Depois disso basta substituir a Rede pelo padrao 255 e o Host pelo padrao 0 , veja o exemplo abaixo.

# Mascaras de Redes

- Classe A : 10.0.12.15   | Mascara : 255.0.0.0
- Classe B : 172.16.0.10 | Mascara : 255.255.0.0
- Classe C : 192.168.0.1 | Mascara : 255.255.255.0

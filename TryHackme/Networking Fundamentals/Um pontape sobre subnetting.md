**Room**: Intro to Lan 
**Task**: 2
**Materia**: Subnetting

**Nota**: Uma subnet eh usado na premissa de dividir uma rede em pedacos para ter uma maior seguranca e organizacao. Formado por um grupo de 4 *octetos* , uma subnet usa o endereco IP de 3 maneiras diferentes:

- Identificar o endereco de rede
- Identificar o endereco de host
- Identificar o gateway padrao

Vamos enteder os tres pontos citados a cima :

**Network Address** - Usado para identificar o comeco de uma rede.

**Host Address** - Usado para identificar um dispositivo dentro de uma rede. 

**Gateway Default** - Aquele dispositivo/computador que faz a comunicacao de todos os outros computadores da rede com a internet ou a comunicacao de todos os computadores entre eles. 


---

<h1 align="center"> Calculo de sub-rede </h1>
Dada as informacoes de um computador a seguir calcule a sub-rede

Endereco IP: 192.168.40.18
Mascara : 255.255.255.240
Gateway:  192.168.40.17

- A primeira coisa que temos que fazer eh achar a **Mascara**
- Achar o **octeto-misto** na Mascara  : Octeto misto eh aquele numero diferente de 0 e 255 .
- Achar o **salto** : O salto eh a quantidade de IP's que cada sub-rede tem (de acordo com a mascara esse numero pode variar) . para achar a do enunciado em especifico -> (240) precisamos fazer ![[Um pontape sobre subnetting 2023-06-02 14.48.23.excalidraw]]
- Achar as sub-redes e ver qual o ip com final 18 se encontra A
- Obs: NAO existe sub-rede impar e broadcast par !
---

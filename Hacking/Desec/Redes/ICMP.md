<h2 align="center">Internet Control Message Protocol </h2>
<hr>


O protocolo ICMP eh um protocolo de alerta por mensagens, ele emite avisos sobre a situacao de rede.

A estrutura basica do ICMP eh simples, composta de tipos e codigos, cada um com sua funcao.

![[mpv-shot0006 2.jpg]]


| TYPE | CODE | CHECKSUM |


| Tipo | Código | Descrição                                                                     |
| ---- | ------ | ----------------------------------------------------------------------------- |
| 0    | 0      | Echo Reply (Resposta de Eco)                                                  |
| 3    | 0      | Destination Unreachable (Destino Inalcançável) - Rede Inalcançável            |
| 3    | 1      | Destination Unreachable (Destino Inalcançável) - Host Inalcançável            |
| 3    | 2      | Destination Unreachable (Destino Inalcançável) - Protocolo Inalcançável       |
| 3    | 3      | Destination Unreachable (Destino Inalcançável) - Porta Inalcançável           |
| 4    | 0      | Source Quench (Supressão de Fonte) - Indica congestionamento de rede          |
| 8    | 0      | Echo Request (Requisição de Eco)                                              |
| 11   | 0      | Time Exceeded (Tempo Excedido) - Tempo de Vida Excedido no Trânsito           |
| 11   | 1      | Time Exceeded (Tempo Excedido) - Tempo de Reassemblagem de Fragmento Excedido |
| 12   | 0      | Parameter Problem (Problema de Parâmetro) - Erro no Cabeçalho IP              |
| 13   | 0      | Timestamp Request (Requisição de Carimbo de Data/Hora)                        |
| 14   | 0      | Timestamp Reply (Resposta de Carimbo de Data/Hora)                            |
| 15   | 0      | Information Request (Requisição de Informação) - Obsoleto                     |
| 16   | 0      | Information Reply (Resposta de Informação) - Obsoleto                         |
| 17   | 0      | Address Mask Request (Requisição de Máscara de Endereço)                      |
| 18   | 0      | Address Mask Reply (Resposta de Máscara de Endereço)                          |
<h2 align="center"> Importancia do ICMP</h2>
<hr>

No exemplo abaixo temos um host cliente utilizando o protocolo UDP tentando se comunicar com uma porta fechada no host servidor.

Lembrando que o protocolo UDP nao possui nenhum tipo de controle, dessa forma o protocolo UDP sozinho nao tem capacidade de avisar sobre oque acontece na comunicacao

 ![[mpv-shot0007 2.jpg]]
 <hr>

Ao enviar um ping para um host inexistente na rede como retorno um **Destination Host Unreacheable** ,indicando que o host de destino nao foi encontrado.

Sem o aviso do protocolo ICMP nao teriamos nenhum retorno sobre o que ocorreu na rede.

![[mpv-shot0008 1.jpg]]

```sh
traceroute -n www.businesscorp.com
```
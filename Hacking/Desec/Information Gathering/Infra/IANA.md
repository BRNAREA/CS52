<h2 align="center">Internet Assigned Numbers Authority</h2>
<hr>

```ad-question
title: Porque isso?

Imagine o seguinte , voce vai atacar um determinado cliente um grande cliente, e voce quer descobrir os blocos de IP - REDE , que sao de propriedade dessa empresa e pra voce descobrir isso , voce precisa entender como que funciona esta estrutura na internet.
```

Responsavel por coordernar alguns dos elementos chaves para manter a internet operacional.

- Gerenciamento dos root servers (Domain Names) - 13 Servidores 
- Coordenacao de numeros IP e ASN (Autonomous System Numbers)
- Registros de protocolos

```ad-info
title: os 13 root servers DNS
| HOSTNAME | IP ADDRESS | MANAGER |
-----------------------------------
| - a.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - b.root-servers.net | 199.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - c.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - d.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - e.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - f.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - g.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - h.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - i.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - j.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - k.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - l.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |
| - m.root-servers.net | 198.41.0.4. | 2001:503:ba3e::2:30 | VeriSign Inc. |

```



<h2 align="center">Netblock x ASN</h2>

<p align="center">Netblock (Bloco de rede)</p>
<p align="center">Um range  ou conjunto de enderecos IPs</p>

<p align="center">
Autonomous System (Sistema autonomo)
<p align="center"> Um ou mais blocos de redes sob o mesmo administrador
</p>

Exemplo:

Se a empresa precisa de um range com 12 IPs ela pode comprar um netblock

Se a empresa precisa ed centenas de enderecos IPs ela pode comprar um ASN

![[mpv-shot0001 1.jpg]]


![[mpv-shot0002 1.jpg]]


IANA > RIR > NIR > OVH > BUSINESSCORP | ENDERECOS IP
IANA > LACNIC > REGISTRO.BR > BUSINESSCROP | DOMINIOS


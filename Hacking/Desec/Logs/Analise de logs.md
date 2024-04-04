<h2 align="center"> Analise de logs like a pro</h2>
<hr>

Se voce identificar um log presente em uma aplicacao , voce pode tirar proveito disso , abaixo vai ter codigos na qual exploram esses logs.

A primeira coisa a ser feita eh entender como funciona o log.
Depois vamos filtrar este log



```sh
wget www.businesscorp.com.br/access.log
cat access.log
wc -l access.log

head -n1 access.log
cat access.log | cut -d " " -f 1 | sort | uniq -c | sort -un

cat access.log | grep "<IP>" | head -n1
cat access.log | grep "<IP>" | tail -n1
```

Utilitarios utilizados:
- [[wget]]
- [[curl]]
- [[wc]] (word count)
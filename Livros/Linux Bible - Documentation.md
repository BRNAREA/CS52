# Documentacao

## Recomendacoes Gerais

###### FIle permissions and attributes

__File systems__ usam __permissioes__ e __atributos__ para regular o level de interacao que aquele processo de systema pode ter com arquivos e diretorios.

> [!WARNING] Quando usado  para propostas de seguranca , permissoes e atributos defendem apenas contra ataques lancados do sistema bootado . Para proteger dados armazenados de atacantes com acesso fisico a maquina , deve-se também implementar a criptografia de dados em repouso. 


---
###### Vendo permissoes
---
Use o comando __ls__ opcao `-l` para ver a permissao (modo de arquivo) setado para conteudos de um diretorio 

````linux
$ ls -l /path/to/directory

total 128
drwxr-xr-x 2 archie archie  4096 Jul  5 21:03 Desktop
drwxr-xr-x 6 archie archie  4096 Jul  5 17:37 Documents
drwxr-xr-x 2 archie archie  4096 Jul  5 13:45 Downloads
-rw-rw-r-- 1 archie archie  5120 Jun 27 08:28 customers.ods
-rw-r--r-- 1 archie archie  3339 Jun 27 08:28 todo
-rwxr-xr-x 1 archie archie  2048 Jul  6 12:56 myscript.sh
````

A primeira coluna e a qual devemos focar . tomando um exemplo do valor `drwxrwxrwx+`, o significado de cada caracter e explicado nas tabelas abaixo.


> [!info] - d ->  O tipo de arquivo , tecnicamente nao faz parte das permissoes.
> - rwx -> Permissoes que o proprietario tem sobre o arquivo.
> - rwx -> Permissoes que o grupo tem sobre o arquivo.
> - rwx -> Permissoes que todos usuarios tem sobre o arquivo.
> - `+` -> Um único caractere que especifica se um método de acesso alternativo se aplica ao arquivo. Quando esse caractere e um espaco , nao existe metodo de acesso alternativo . O caractere `.` indica um arquivo com contexto de seguranca , mas  sem outros metodos de acesso .Um arquivo com outra combinacao de metodos de acesso alternados é marcado com um caractere `+` , por exemplo em caso de __Lista de Controles de Acessos__ .

Cada uma das tres triades de permissao (rwx no exemplo acima) pode ser composta pelos seguintes caracteres :

---
#### Permissao de leitura ( primeiro caractere) : 

`-` -> 
Efeito em arquivos : O arquivo nao pode ser lido.
Efeito em diretorios : O conteudo do diretorio nao pode ser mostrado.

`r` -> 
Efeito em arquivos : O arquivo pode ser lido.
Efeito em diretorios : O conteudo do diretorio pode ser mostrado.

---

#### Permissao de escrita ( segundo caractere ) :
`-` ->
Efeito em arquivos : O arquivo nao pode ser modificado.
Efeito em diretorios : O conteudo do diretorio nao pode ser modificado.

`w` ->
Efeito em arquivos : O arquivo pode ser modificado 
Efeito em diretorios : O conteudo do diretorio pode ser modificado ( criar novos arquivos ou diretorios; 
renomear ou deletar arquivos ou diretorios existentes);
requer que a permissao de execucao tambem seja definida , caso contrario , essa permissao nao tera efeito.

---
#### Permissao de execucao (terceiro caractere)
`-` -> 
Efeito em arquivos : O arquivo nao pode ser executado.
Efeito em diretorios : O diretorio nao pode ser acessado com `cd`.

`x` -> 
Efeito em arquivos : O arquivo pode ser executado 
Efeito em diretorios :O Diretorio pode ser acessado com `cd`; essa e a unica permissao pequena que em pratica pode ser considerada ser "herdada" de um diretorio ancestral , de fato , se algum diretorio no caminho nao tiver o `x` bit definido , o arquivo ou diretorio final tambem nao podera ser acessado , independentemente de suas permissoes .

`s` ->
Efeito em arquivo : O bit __setuid__ quando encontrado na triade usuario ; o _setgid_ quando encontrado na triade grupo; nao e encontrado nas outras triades ; tambem imploca que x e definido.

`S` -> mesmo que o bit `s` , mas `x` nao esta setado , raras em arquivos regulares, e inutilizaveis em diretorios.
`t` -> o bit __sticky__ pode apenas ser encontrado em outras triades ; e tambem implica que x e definido.
`T` -> mesmo que `t` , mas `x` nao esta definido ; rara em arquivos regulares

Exemplos para clarificar :

`drwx------`
Archie tem acesso total ao diretorio Documents . Podendo listar , criar , renomear ou deletar arquivos em Documents , Independemente da permissao do arquivo . Sua habilidade de acesso a um arquivo depende das suas permissoes sobre o arquvio

`dr-x------`
Archie tem acesso exceto : criar , renomear , deletar QUALQUER arquivo . Eles podem listar os arquivos e ( se a permissao permitir-lo ) pode acessar um arquivo existente ao Documents.

`d-wx------`
Archie nao pode fazer `ls` no diretorio `Documents` mas se eles souberem o nome de um arquivo de um arquivo existente entao eles podem listar , renomear , deletar ou ( se a permissao do arquivo permitir) acessa-lo. Tambem , eles sao aptos a criar novos arquivos .

`d--x------`

Archie e apenas capaz de (se a permissao do arquivo permitir ) acessar aqueles arquivoos de `Documentos` 
 que eles conhecem. Eles nao pode listar arquivos ja existentes ou criar , renomear , deletar , algum deles.

Voce tem que ter em mente que elaboramos permissoes em diretorios e isso nao tem nada 
a ver com as permissoes de arquivos individuais

Quando voce cria um novo arquivo  é diretorio que muda . Isso  é o porque voce precisa escrever a permissao do diretorio

`-rw-r--r--`

Aqui nos podemos ver que a primeira letra nao  é `d`mas `-` . Entao sabemos que  é um arquivo , e nao um diretorio . A proxuma permissao do proprietario sao `rw-` entao o proprietario tem a capacidade de ler e escrever e nao executar. This pode parecer estranho 
que o proprietario nao tenha todas as tres permissoes , mas a permissao `x` nao é necessaria como em um arquivo de texto , pra ler por um editor de texto basta um Gedit , EMACS , ou software como R , e nao um executavel por si so ( se contivesse algo como codigo de programacao puthon poderia muito bem ser ) .

As permissoes de grupo sao definidas para `r--` , entao o grupo tem a capacidade de ler o arquivo mas nao escrever/editar de qualquer maneira -- e essencia como configurar algo para apenas-leitura . Podemos ver que as mesmas permissoes sao aplicadas para todo mundo tambem.










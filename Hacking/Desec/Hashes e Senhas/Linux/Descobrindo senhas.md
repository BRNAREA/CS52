<h1 align="center">Descobrindo Senhas com John</h1>
<hr>

No sistema que a gente invadiu vamos ler o arquivo `passwd` e o arquivo `shadow` e salvar o conteudo desse arquivo.s

```sh
cat /etc/passwd > passwd
cat /etc/shaodow > shadow
```

Fazemos isso por que precisamos deixar o arquivo em um padrao que a ferramenta `john` entenda.

Existe um utilitario na pacote do `john` que se chama `unshadow` entao oque a gente vai fazer eh fazer o `unshadow` do `shadow` basicamente haha 😂.

```sh
unshadow passwd shadow > hashes
```

Basicamente oque essa ferramenta fez foi pegar o conteudo da senha e adicionar na parte do arquivo `/etc/passwd`

Feito isso vamos executar

```sh
john hashes
```

Podemos fazer isso localmente tambem para vermos

```sh
unshadow /etc/passwd /etc/shadow > myhash
john myhash
```
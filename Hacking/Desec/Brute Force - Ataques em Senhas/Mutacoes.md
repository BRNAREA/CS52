<h1 align="center">Gerando mutacao na Wordlist</h1>
<hr>

```ad-question
title: Oque seria mutacao?

Seria uma serie de regras que vao aplicar variacoes na sua wordlist
usando o john podemos fazer isso

/etc/john/john.conf
Wordlist mode rules #local para adicionar regras
john --wordlist=lista --rules --stdout > mutacao

Exemplos:
odraciR
7Rick7
Roger@10
```

<hr>
### Crunch


| Gerador | CRUNCH                |
| ------- | --------------------- |
| %       | Digitos               |
| ^       | Caracteres Especiais  |
| @       | Caracteres Minusculos |
| ,       | Caracteres Maiusuclos |


Podemos informar pra ele gerar um padrao de senhas
Gerador de wordlists

crunch 10 10 -t rogerio^%% -o wordlist
crunch 1414 -t Gbusiness^^%%% -o wl-gb

<hr>

### Cewl
cewl <site> -m 5


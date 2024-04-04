<h1 align="center"> Key Space - Brute Force</h1>
<hr>

O tipo de brute force que vai esgostar todas as possiblidades ate encontrar a senha. Muito util quando o padrao utilizado eh identificado.

Exemplo didatico:
PIN 4 Digitos
Senha 6 Digitos numericos

Exemplo real:
Caso: Token(A2F3C5)


Se gerarmos uma wordlist com o padrao , nao tem como nao termos a senha nessa wordlist, entao se o sistema for sucetivel a brute force e voce identificar um padrao e gerar um key space bruteforce a senha vai estar la. Vai ser so questao de tempo.

Podemos utilizar entao o <span style='color:var(--mk-color-red)'>crunch</span> para gerar essa wordlist nesse padrao e esgotar todas as possibilidades.

```sh
crunch 4 4 0123456789 -o pin
crunch 6 6 -f charset.lst numeric -o pin
```

```ad-info

diretorio do crunch
/usr/share/crunch/

```
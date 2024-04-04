<h1 align="center"> Modulos Auxiliares - METASPLOIT</h1><hr>

Iniciando o metasploit:
```sh
msfconsole
```

Mostrar comandos que podemos usar:

```sh
msf5> show -h
msf5> show payloads
```

Para utilizar algum modulo:

```sh
msf5> use auxiliary/scanner/portscan/tcp
msf5> auxliary(scanner/portscan/tcp) >
```

Quando ele fica em vermelho : auxliary(<mark style='background:var(--mk-color-red)'>scanner/portscan/tcp</mark>) significa que a gente esta usando esse modulo.

Para a gente visualizar a gente pode dar um `info`

```sh
msf5>auxliary(scanner/portscan/tcp) > info
```

Podemos mostrar as opcoes:

```sh
msf5>auxliary(scanner/portscan/tcp) > show options
```

Para setar alguma opcao como o alvo por exemplo:

```sh
msf5>auxliary(scanner/portscan/tcp) > set RHOSTS <IP>
auxliary(scanner/portscan/tcp) > show options
```

Para executar este scan:

```sh
auxliary(scanner/portscan/tcp) > run
```

Pesquisar algo:

```sh
search -h
```

Voltar:

```
back
```



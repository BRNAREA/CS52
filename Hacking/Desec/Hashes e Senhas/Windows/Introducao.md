<h1 align="center">Introducao aos hashes e senhas em sistemas Windows</h1>
<hr>

O windows possui diversas versoes de sistemas desde WORKSTATIONS , DESKTOP , SERVIDORES (WINDOWS SERVER) e desde sistemas antigos a sistemas mais modernos a gente tem algumas particularidades que a gente precisa entender quando vai obter hashes desses sistemas.

<h2 align="center">ARQUIVOS</h2>
<hr>

```ad-info
title: Arquivos de configuracao do Windows

SAM - Security Account Manager (Windows)
- Armazena as contas de usuarios
- %SystemRoot%system32/config/sam

NTDS.DIT (Windows Server / Active Directory )
- Armazena dados do AD incluindo as contas de usuarios
- %SystemRoot%/ntds/ntds.dit

SYSTEM
- Arquivo do sistema necessario para decriptar o SAM/NTDS.DIT
- %SystemRoot%/system32/config/system

```


1. O primeiro arquivo que a gente precisa conhecer no Windows eh o arquivo <mark style='background:var(--mk-color-purple)'>SAM</mark> - Security Account Manager , esse arquivo eh responsavel  por armazenar as contas de usuarios. (Windows XP), quando a gente fala de servidores como Windows Server 2019,2019 que tenha um contralador de dominio ou <mark style='background:var(--mk-color-purple)'>AD</mark> voce vai ter uma outra estrutura que vai ser o arquivo NTDS.DIT

2. A estrutura dele fica em Windows/ntdds e dentro deste diretorio vai ter um arquivo chamado ntds.dit dentro desse arquivo ele armazena varios dados do <mark style='background:var(--mk-color-purple)'>AD</mark> incluindo as contas de usuarios , entao sempre quando a gente fala  de obter hashes em controladores de dominio em <span style='color:var(--mk-color-teal)'>Windows Server</span> que tem <span style='color:var(--mk-color-teal)'>"AD"</span> a gente vai mirar nesse arquivo , a gente vai precisar obter esse arquivo do servidor para que a gente possa extrair os hashes e as contas de usuarios existentes nesse servidor.


3. Temos tambem o Arquivo <span style='color:var(--mk-color-blue)'>System</span> que tambem eh muito importante , *normalmente tanto o arquivos <span style='color:var(--mk-color-teal)'>SAM</span> quanto o  <span style='color:var(--mk-color-teal)'>NTDS.DIT</span> sao encriptados , o Windows encripta eles e a chave pra gente decriptar esse arquivo fica dentro de um outro arquivo do sistema que eh o arquivo <span style='color:var(--mk-color-blue)'>System</span>*. Por isso que normalmente quando a gente vai obter hashes a gente precisa obter esses arquivos diretamente voce precisa sempre ter o <span style='color:var(--mk-color-teal)'>SAM</span>  e o <span style='color:var(--mk-color-teal)'>System</span> ou <span style='color:var(--mk-color-turquoise)'>NTDS.DIT</span> e o <span style='color:var(--mk-color-turquoise)'>System</span> . Porque o System eh onde o software normalmente vai buscar uma chave para decriptar depois o arquivo SAM e o arquivo NTDS.DIT.

```ad-caution
title: Problemas
Mas qual o problema temos aqui? o primeiro problema eh que quando a gente tem acesso ao sistema (administrativo) vai para dentro do diretorio e tentar copiar para sua maquina, fazer download e etc.. voce nao vai conseguir com o sistema em execucao , isso porque eles sao protegidos o Windows protege e bloqueia esses arquivos.
```

```ad-hint
title: Solucoes
Pra isso temos algumas solucoes.
Uma delas provavelmente para um ataque remoto ficaria inviavel eh um acesso fisico a maquina (hardware) desligando o mesmo , fazendo um boot live CD e montar a estrutura do Windows pra capturar esses arquivos , mas isso seria inviavel pra um ataque remoto.

2.Mas para ataques remotos podemos fazer o seguinte: Em sistemas mais antigos como Windows XP ele normalmente armazena um diretorio de Backup que seria o 'Repair' em:
`C:\Windows\repair (apenas sistemas antigos como XP/2003)` , nem sempre este backup sera atualizado.

3.Em sistemas recentes como Windows 10 podemos salvar diretamente do registro do Windows , podemos usar o `reg` para fazer uma consulta no registro , salvar entradas do registro , adicionar enfim...tudo via linha de comando , isso claro com acesso administrativo ao sistema voce pode fazer o download das entradas diretamente do registro do Windows ai voce baixa o SAM e baixa o System.

- Salvar diretorio do registro do windows (Desde versoes antigas a versoes recentes) <- 
Ex: reg save hklm/sam

4.Podemos tambem utilizar para versoes recentes uma tecnica de copia sombra do volume , ou seja , voce faz uma copia sombra do volume todo e qunaod fazemos essa copia tendo acesso administrativo, acessamos oque queremos (NTDS.DIT) e excluimos a copia.
- Copia sombra do volume (Versoes mais recentes)<-
Ex: vssadmin

```

<h3 align="center">Ataques</h3>
<hr>

Uma vez que obtemos os arquivos , ou seja , obtemos o NTDS.DIT do Windows Server ou Windows normal que obtivemos o SAM e o System a gente vai obter os hashes que tem dentro desses arquivos e depois tentar quebrar esses hashes.

#### Outras Tecnicas

- Senhas em memoria/cache - Utilizar tecnicas para obter senhas em cache ou na memoria do Sistema.
- Pass the Hash - Tecnica para utilizar um hash sem precisar quebra-lo.
- Captura de hashes na rede.

Podemos utilizar softwares para obter senhas em cache, senhas da memoria ou quando voce nao consegue quebrar esse Hash mas existe uma tecnica chamada Pass the Hash (Passe o Hash) para se autenticar em um determinado sistema e consegui acessar o sistema mesmo sem saber a senha , e capturar hashs na rede.

<h4 align="center">Exemplos de Hashes no Windows</h4>
<hr>


| Usuario                                                       | ID                                                 | LM (LAN MANAGER)                                                                     | NTLM (NT LAN MANAGER)                                                              |
| ------------------------------------------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------- |
| <span style='color:var(--mk-color-teal)'>Administrador</span> | <span style='color:var(--mk-color-red)'>500</span> | <span style='color:var(--mk-color-green)'>aad3b435b51404eeaad3b435b51404ee</span>... | <span style='color:var(--mk-color-purple)'>aad3b435b51404eeaad3b435b51404ee</span> |
| Convidado                                                     | 501                                                | aad3b435b51404eeaad3b435b51404ee                                                     | aad3b435b51404eeaad3b435b51404ee                                                   |
| HelpAssistant                                                 | 1000                                               | aad3b435b51404eeaad3b435b51404ee                                                     | aad3b435b51404eeaad3b435b51404ee                                                   |
| rafaela                                                       | 1005                                               | aad3b435b51404eeaad3b435b51404ee                                                     | aad3b435b51404eeaad3b435b51404ee                                                   |

aad3b435b51404eeaad3b435b51404ee == vazio (significa que nao esta usando LM) ou que nao esta usando ele.
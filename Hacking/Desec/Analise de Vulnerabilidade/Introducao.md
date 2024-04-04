<h2 align="center">Introducao</h2>
<hr>

Neste modulo iremos falar sobre analise de vulnerabilidade.
A ideia aqui e trazer um conceito , nao so da fase de pentest , porque isso tudo eh um processo , a gente tem : Information Gathering , Scanning , Enumeration ... e dentro de cada uma destas fases coletamos um monte de informacoes .


Lembrando que analise de vulnerabilidade eh diferente de pentest , podemos fazer isso tanto de forma manual como de forma automatizada.

Veja mais em [[Tipos de Pentest de Seguranca]]
<h2 align="center"> Fase  de Analise de Vulnerabilidade </h2>
<hr>

Durante o processo de um __pentest__ chegaremos  a __fase de analise de vulnerabilidade__, ou melhor dizendo , fase onde vamos procurar por possiveis vulnerabilidades existentes no ambiente testado.

As vulnerabilidaes podem aparecer em varios locais, em aplicacoes, software, sistema operacional, servicos, configuracoes, comunicacao, ou seja, nao existe uma receita de bolo mas sim __um processo__.

Seguindo nosso metodo de trabalho:

- [x]  Information Gathering | Coleta de informacoes
- [x] Scanning | Varredura
- [x] Enumeration | Enumeracao
- [ ] Vulnerability Analysis | Analise de Vulnerabilidade
- [ ] Exploitation | Exploracao
- [ ] Post Exploitation | Pos exploracao

<h2 align="center">Processo</h2>
<hr>

Para realizar o __processo de analise de vulnerabilidade__ de forma __manual__ recomendo utilizar o seguinte processo:

1. Identificar o possivel SO -> Scanning/enumeracao
2. Identificar a possivel versao do software / aplicacao / sistema -> Scanning/enumeracao
3. Buscar por vulnerabilidades  conhecidas
4. Tentar identificar vulnerabilidade ainda nao conhecidas
5. Se possivel tentar outros tipos de ataques (exemplo: Brute force)*

Base de dados de vulnerabilidades e exploits
https://www.exploits-db.com -> base de dados de exploits
https://www.securityfocus.com/vulnerabilities ->  base de dados de vulnerabilidades
https://www.cvedetails.com/ -> base de dados de vulnerabilidades
https://nvd.nist.gov/vuln/search -> base de dados de vulnerabilidades
https://www.rapid7.com/db/?q=&type= -> base de dados de vulnerabilidades
https://packetstormsecurity.com/files/tags/exploit/ -> base de dados de exploit

searchsploit - utilitario para busca  de exploits (exploit-db)

<h1 align="center"> Pesquisa manual por vulnerabilidade </h2>
<hr>


![[mpv-shot0001 6.jpg]]


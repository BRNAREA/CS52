<h1 align="center">Metodologia para Mapeamento de portas</h1>
<hr>

Porque vamos falar sobre isso ?

Uma vez que temos uma metodologia pra realizar esse tipo de tecnica , vamos conseguir aplicar isso nao somente para pentest direcionado pra um host , quanto outro tipo de pentest.

Voce no escopo , quando for realizar um teste de seguranca em um ambiente , rede ou pentest externo , enfim .. a parte de mapeamento de portas sempre vai estar envolvida , vai chegar  o ponto que voce precisa identificar quais portas estao abertas no alvo para identificar quais os servicos , sistemas operacionais etc..

Temos duas linhas de atuacao, uma delas eh quando o cliente nos passa um escopo especifico e fala que precisa testar um numero de host fixo , e ai precisamos testar esses (10 por exemplo) hosts , fazer scan nos 10 hosts completo e ai isso a gente chama de `TCP HOST SCAN` na qual a gente vai fazer um mapeamento de portas tcp completo pra identificar todas as portas tcp abertas naquele host.

Depois o mesmo se aplica para o `UDP HOST SCAN` , porque muita gente esquece de testar UDP e ai varios servicos rodam em cima do UDP , por exemplo : [[SNMP]] , [[DNS]] , NTP. E esses servicos podem conter vulnerabilidades tambem , validar tanto tcp quanto UDP.

![[mpv-shot0004 2.jpg]]

Agora imagine um outro cenario , seja ele externo ou interno onde voce esta alocado na base do cliente , e ele te coloca em uma rede cabeada ou wireless voce comeca o pentest daquele ponto de acesso, agora imagine que essa rede tem 5 mil computadores (Rede grande) e voce tem que mapear hosts ativos e que tenham vulnerabilidades , mas pra isso voce precisa descobrir servicos ativos rodando, pra identificar os servicos voce precisa identificar as portas ,agora voce tem que realizar o `TCP HOST SCAN` e `UDP HOST SCAN ` em cada um dos hosts.. quanto tempo isso nao levaria nao eh ?  voce ficaria semanas , meses no cliente fazendo somente essas execucoes host por host .

Entao nesses tipos de pentest voce tem que ter tecnicas para otimizar seu tempo, uma delas seria o [[Network Sweeping]] , varredura na rede
![[mpv-shot0005 1.jpg]]
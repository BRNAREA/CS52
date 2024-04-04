<h1 align="center">Ataques em senhas</h1>
<hr>

Vamos aprender a construir nossa propria wordlist , personaliza-las e construir nossa propria ferramenta para brute force. Vamos entender alguns conceitos importantes antes da gente comecar na forma pratica

```ad-question
title: Oque eh ataque de forca bruta?

Um ataque brute force ou forca bruta eh quando a gente tenta descobrir senhas atraves de tentativo e erro
```

Oque faria com que esse sistema ou essa aplicacao tivesse uma condicao de ataque de forca bruta ?

Se esse sisetma nao tiver nenhum tipo de limite.

Ex : Se eu tento autenticar minha conta 3 vezes com a senha errada e o sistema nao faz nada , nos temos uma condicao de ataque de forca bruta. Isso porque podemos tentar dezenas , centenas de vezes ate acertamos.

Se o sistema tem um bloqueio em segundos podemos mesmo assim fazer o brute force a cada x segundos.

```ad-info
Outros detalhes de brute force eh que tudo que voce envia pro servidor ou aplicacao , esta gerando um log no servidor , e ataques de forca bruta normalmente  sao bem ruidosos ,pois geram bastante logs, dependendo de como eh o sistema interno da empresa eles podem facilmente detectar voce, isso depende da equipe analista.
```

Padroes:
Ataque de guessing: Ataque de adivinhacao , o atacante analisaria o perfil da empresa e usuario , como : comportamento , gostos e com base nisso ele tenta prever a sua senha.

Credenciais Default: Ataque de credenciais padroes do sistema, carregando uma wordlist com senhas e usuarios padroes fazendo ataque

Leaks: Banco de dados vazados da empresa recentemente

![[mpv-shot0001 12.jpg]]


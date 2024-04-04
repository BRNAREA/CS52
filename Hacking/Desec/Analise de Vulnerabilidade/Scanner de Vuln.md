

```ad-tip
**Sao ferramentas capaz de automatizar o processo de descoberta de vulnerabilidades**
```

Vamos conhecer algumas ferramentas de mercado bem conhecidas.

- Nessus (free e comercial)
- Qualys (comercial)
- OpenVAS (Open Source)


```ad-question
title: Como funciona?
Um bom scanner de vulnerabilidades vai tentar automatizar o processo da seguintes forma

1. Tenta identificar se o host esta ativo
2. Realiza um portscan
3. Tenta identificar o sistema operacional
4. Tenta identificar os servicos encontrados
5. Faz a verificacao de vulnerabilidades de acordo com sua base de vulnerabilidades
```

<h3 align="center" >Vantagens e Desvantagens</h3>

```ad-success
title: VANTAGENS
- Analisa uma grande quantidade de vulnerabilidades conhecidas em pouco tempo em diversos hosts simultaneamnete
- Ajuda a realizar o gerenciamento de patches
- Pode ser usado para ajudar em processos de auditoria e compliance
```

```ad-failure
title: DESVANTAGENS
- Pode gerar falsos positivos (informar que existe uma vulnerabilidade onde nao existe)
- Gera falsos negativos (nao detecta uma vulnerabilidade existente)
- Consome poder computacional]
- Gera bastante ruido na rede/host
```


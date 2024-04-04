O HTTPS funciona similar ao HTTP contanto que agora a conexao tem SSL , uma camada criptografada.

```ad-info
O HTTPS funnciona por default na porta 443 ou 8443 (versao alt)
```

Se nos tentarmos uma conexao com um alvo https utilizando uma conexao sem criptografia como http , nao vamos ter exito em nos conectarmos com o alvo , entao precisamos utilizar algum servico/utilitario que tambem entenda a criptografia.

Um utilitario muito legal nesse caso eh o `openssl`

Exemplo para estabelecermos esse mesmo tipo de comunicacao usando openssl:

```bash
openssl s_client -connect tesla.com:443
```

Outro detalhe importante aqui, e para detectarmos WAFs, Proxys ou qualquer intermediarios do nosso alvo, por isso eh interessante utilizarmos o HTTP 1.1 e o Host

Sempre utilizaremos o `Host` para que nao conversemos diretamente com o proxy ou waf do servidor.

> [!tldr] TTL
> Em alguns WAF's ou Proxys de servidores havera um TTL ou tempo limite para se fazer uma requisicao.

Sao detalhes importantes porque quando tentamos conectar com aquele endereco aquele site , aquele IP , em alguns casos vamos estar falando com o Proxy ou WAF  e nao com o Servidor que eh o que queremos atingir.

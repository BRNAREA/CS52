# Cross Origin Resource Sharing (CORS)

<u><a href="https://developer.mozilla.org/pt-BR/docs/Glossary/CORS">CORS</u></a> - Cross-Origin Resource Sharing (Compartilhamento de recursos com origens diferentes) é um mecanismo que usa cabeçalhos adicionais <u><a href="https://developer.mozilla.org/pt-BR/docs/Glossary/HTTP">HTTP</a></u> para informar a um navegador que permita que um aplicativo Web seja executado em uma origin (domínio) com permissões para acessar recursos selecionados de um servidor em uma origem distinta.

Um aplicativo Web executa uma __requisição ___cross-origin___ HTTP__ ao solicitar um recurso que tenha origem diferente (domínio , protocolo e porta ) da sua própria origem .

Um exemplo de requisição _cross-origin_ : o código JavaScript _frontend_ de um aplicativo Web disponível em `http://domain-a.com` usa <u><a href="https://developer.mozilla.org/pt-BR/docs/Web/API/XMLHttpRequest">XMLHttpRequest</a></u> para fazer uma requisição para `http://api.domain-b.com/data.json`.

Por motivos de segurança , navegadores restrigem requisições _cross-origin_ HTTP iniciadas por scripts. Por exemplo , ``XMLHttpRequest`` e <u><a href="https://developer.mozilla.org/pt-BR/docs/Web/API/Fetch_API">Fetch API</u></a> seguem a [[Política de mesma origem]]
(_same-origin-policy_ ) . Isso significa que um aplicativo web que faz uso dessas APIs só podem fazer solicitações para recursos de mesma origem da qual o aplicativo foi carregado , a menos que a resposta da outra origem inclua os cabeçalhos CORS corretos.



O mecânismo CORS  suporta requisições seguras do tipo _cross-origin_ e transferências de dados entre navegadores  e servidores web. Navegadores modernos usam o CORS em uma API contêiner como `XMLHttRequest` ou Fetch , para ajudar a reduzir os riscos de requisições _cross-origin_ HTTP.

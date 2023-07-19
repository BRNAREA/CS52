#           Same-origin Policy
A <u><a href="https://developer-mozilla-org.translate.goog/en-US/docs/Web/Security/Same-origin_policy?_x_tr_sl=auto&_x_tr_tl=pt&_x_tr_hl=pt-BR">política de mesma origem</u></a> é um mecanismo de segurança crítico que restringe como um documento ou script carregado por uma __origem__ podem interagir com um recurso de outra origem.

Ou seja é uma restrição de segurança que delimita o contéudo Web com oque o código JavaScript pode interagir.

Ajuda a isolar documentos potencialmente maliciosos , reduzindo possíveis vetores de ataque. Por exemplo , ele impede que um site malicioso na internet execute JS em um navegador para ler dados de um serviço de webmail de terceiros (no qual o usuário está conectado) ou de uma intranet da empresa (que é protegida do acesso direto do invasor por não ter um endereço IP público) e retransmitir esses dados para o invasor.

### Definição de uma mesma origem

Dois URLs têm a _mesma origem_ se o <u><a href="https://developer.mozilla.org/en-US/docs/Glossary/Protocol">Protocolo</u></a> , a <u><a href="https://developer.mozilla.org/en-US/docs/Glossary/Port"> porta</u></a> (se especificado) e o <u><a href="https://developer.mozilla.org/en-US/docs/Glossary/Host"> host </u></a> forem os mesmos para ambos . Você pode ver isso referenciado como a "tupla esquema/host/porta" ou apenas "tupla".(Uma "tupla" é um conjunto de itens que juntos formam um todo - uma forma genérica para duplo/triplo/quádruplo/quíntuplo/etc).

A tabela a seguir fornece um exemplo de comparações de origem como URL
``http://store.company.com/dir/page.html``

![[Pasted image 20220712162228.png]]

### Quais solicitações usam o CORS ?

- chamadas `XMLHttpRequest` ou `Fetch API` pela comunicação  entre origens diferentes , tal como discutido acima.
- Web Fonts (para o uso de fontes pelo _cross-domain_ em `@font` do CSS).
- ``Texturas WebGL``
- _Frames_ de imagens/vídeos desenhados em uma tela usando `drawImage()`.

Um script só pode ler as proprieades de janelas e documentos que tenham a mesma origem do documento que contém o script

É importante entender que a origem do script em si é irrelevante para a política de mesma origem : o que importa é a origem do documento no qual o script está incorporado .

A _política de mesma origem_  também se aplica aos pedidos [[Explicando o HTTP]] de scripts feitos com o objeto `XMLHttpRequests` 

Elá e extremamente necessaria para impedir que scripts roubem informações privilegiadas.

Sem essa restrição , um script mal-intencionado (Carregado atráves de um firewall em um navegador de uma intranet corporativa segura) poderia abrir uma janela vazia , tentando  enganar o usuário e fazê-lo usar essa janela para procurar arquivos na intranet. Então o script mal-intencionado leria o conteúdo dessa janela e o enviaria para o seu próprio servidor. 
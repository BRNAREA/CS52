`puppeteer` é um _produto_ para automação de navegadores. Quando instalado, ele baixa uma versão do Chrome, que ele dirige usando `puppeteer-core`- A . (í a , , , , , ínte , . Ser um produto do usuário final, `puppeteer`automatiza vários fluxos de trabalho usando razoável padrões [que podem ser personalizados](https://pptr.dev/guides/configuration).


`puppeteer-core` é uma _biblioteca_ para ajudar a conduzir qualquer coisa que suporte DevTools Protocolo. Ser uma biblioteca, `puppeteer-core`é totalmente conduzido através de sua interface programática que implica que não há incumprimentos são assumidos e `puppeteer-core`Não baixar o Chrome quando instalado.

- Biblioteca Node.js que fornece uma API de alto nivel para controle do Chrome sobre o devtools
- Corre em modo headless ou headful
- Funcionalidades manuais do chrome como:
	-  Screencshots e PDFS
	-  Rastejar um SPA  e gerar seu conteudo pre-renderizado
	-  Possibilidade de automatizar envios de formularios , teste de UI , Entrada de Input etc..
	- Criacao de ambientes de testes automatizados usando JS latest
	- Diagnositico com problemas de desempenho no site por meio de "trace timeline"
	- Compatibilidade com extensoes do chrome.

---
#### Configuração

O puppeteer tem um padrao que pode ser personalizado atraves de um arquivo de configuracao.

Por exemplo, para alterar o diretório de cache padrão que o Puppeteer usa para instalar browsers, pode adicionar um `.puppeteerrc.cjs`( ou `puppeteer.config.cjs`) no raiz da sua aplicação com o conteúdo

```js
const {join} = require('path'); 
/** 
* @type {import("puppeteer").Configuration} 
*/

module.exports = { 
    // Changes the cache location for Puppeteer.  
    cacheDirectory: join(__dirname, '.cache', 'puppeteer'),
};
```

OBS: Depois de adicionar o arquivo de configuração, você precisará remover e reinstalar `puppeteer`para que isso entre em vigor.


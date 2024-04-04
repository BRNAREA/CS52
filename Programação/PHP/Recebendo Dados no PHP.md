>[!QUESTION]
> -> Como receber dados no PHP ?

Primeiro de tudo , para todo recebimento de *dados* no PHP nos precisamos de um formulario no HTML para que seja possivel receber esses *dados* no nosso arquivo.php.

> [!CAUTION]
> Na nossa tag de form do HTML precisamos de 2 atributos em especifico para poder receber esse dados , sao eles o atributo : "method" e o "action".

No atributo __method__ podemos passar alguns metodos que definirao o tipo do envio das nossas informacoes .. 

Existem varios metodos mas , os mais importantes sao __GET__ e __POST__

Vamos dar uma breve explicacao sobre cada metodo , caso queira saber mais sobre os metodos veja na secao [[Metodos de Requisicao]] .. Vamos la entao..

---

O metodo __GET__ e um metodo de pegar certas informacoes , do ingles , GET significa PEGAR ou seja ele pode pegar certas informacoes , mas tambem podendo enviar sem nenhum problema.

> [!WARNING]
> O metodo GET envia as informacoes no cabecalho da URL ! Podendo ser INSEGURO a dados sensiveis , nao recomendamos enviar dados por esse metodo !.

---

O metodo __POST__ e um metodo de envio de informacoes por CORPO , do ingles POST significa POSTAR algo ou alguma coisa , ou seja esse metodo foi especificamente feito para enviar informacoes porem de uma forma bem mais segura uma vez que as informacoes enviadas por este metodo nao serao exibidas na URL da pagina.. :)

>[!INFO]
>O metodo POST e um metodo amplamente utilizado para envio de informacoes sensiveis , mas podendo ser mais lento que o metodo GET por causa do tempo de seguranca do proprio metodo.



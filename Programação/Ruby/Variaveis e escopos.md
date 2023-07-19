
---  
<h1 align="center">VARIÁVEL LOCAL</h1>

> [!INFO]
>  É declarada com a primeira letra do seu nome sendo uma letra **minuscula** ou _sublinhado_

<p align="center">Pode ser acessada apenas onde foi criada. Por exemplo , se você definir uma variável local dentro de uma classe ela estará disponível apenas dentro desta classe, se a definiu dentro de um método , conseguirá acessá-la apenas dentro deste método e assim por diante.</p>

---

<h1 align="center"> VARIÁVEL GLOBAL</h1>

> [!INFO]
> <p align="center"><b>Declarada com prefixo $.</p>


<p align="center">Pode ser acessada em qualquer lugar do programa.
Seu uso é <b>FORTEMENTE DESENCORAJADO</b> pois além de ser visível em qualquer lugar do código , também pode ser alterada em inúmeros locais ocasionando dificuldades no rastreamento de bugs.
</p>

---

<h1 align="center"> VARIÁVEIS DE CLASSE</h1>

> [!INFO]
> <p align="center"> <b> É declarada com o prefixo @@.</b></p>

<p align="center">Pode ser acessada em qualquer lugar da classe onde foi declarada e seu valor é compartilhado entre todas as instâncias de sua classe </p>

---

<h1 align="center">VARIÁVEIS DE INSTÂNCIAS</h1>

> [!INFO]
> <p align="center"><b>Seu nome começa com o símbolo @.</b></p>

<p align="center">Semelhante a variável de classe , tendo como única diferença o valor que não é compartilhado entre todas as instâncias de sua classe.</p>

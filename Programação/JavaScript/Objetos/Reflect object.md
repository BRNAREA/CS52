Reflects é um objeto no JavaScript que fornece métodos para interagir com propriedades de objetos de uma maneira mais controlada e segura. É semelhante ao objeto `Object`, mas oferece métodos adicionais que permitem maior controle sobre as propriedades e comportamentos de objetos.

Aqui estão alguns exemplos de uso dos métodos Reflect:

1.  `Reflect.get()`: Este método permite obter o valor de uma propriedade em um objeto. Por exemplo:

javascriptCopy code

`let obj = {name: 'John', age: 30}; let name = Reflect.get(obj, 'name'); console.log(name); // 'John'`

2.  `Reflect.set()`: Este método permite definir o valor de uma propriedade em um objeto. Por exemplo:

javascriptCopy code

`let obj = {name: 'John', age: 30}; Reflect.set(obj, 'name', 'Jane'); console.log(obj.name); // 'Jane'`

3.  `Reflect.has()`: Este método permite verificar se uma propriedade existe em um objeto. Por exemplo:

javascriptCopy code

`let obj = {name: 'John', age: 30}; let hasName = Reflect.has(obj, 'name'); console.log(hasName); // true`

4.  `Reflect.deleteProperty()`: Este método permite remover uma propriedade de um objeto. Por exemplo:

javascriptCopy code

`let obj = {name: 'John', age: 30}; Reflect.deleteProperty(obj, 'name'); console.log(obj); // {age: 30}`

5.  `Reflect.defineProperty()`: Este método permite definir uma propriedade em um objeto com um determinado comportamento, como se ela fosse acessível ou não. Por exemplo:

javascriptCopy code

`let obj = {}; Reflect.defineProperty(obj, 'name', {   value: 'John',   writable: false }); obj.name = 'Jane'; console.log(obj.name); // 'John'`

Esses são apenas alguns dos métodos disponíveis no objeto Reflect. Você pode encontrar mais informações sobre os métodos disponíveis na documentação da Mozilla.
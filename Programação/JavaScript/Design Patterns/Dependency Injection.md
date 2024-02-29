Injeção de dependência (ou Dependency Injection, em inglês) é um padrão de projeto de software utilizado na programação orientada a objetos para reduzir o acoplamento entre classes e aumentar a flexibilidade e a reutilização de código.

Basicamente, a injeção de dependência consiste em injetar (ou passar) as dependências necessárias a uma classe ou objeto em vez de criar essas dependências dentro da classe. Isso significa que a classe não precisa conhecer os detalhes de implementação das suas dependências, apenas precisa saber como utilizá-las.

Por exemplo, em vez de criar um objeto dentro da classe para acessar um banco de dados, a classe receberia um objeto do tipo "BancoDeDados" já criado por outra classe, por exemplo, por meio de um construtor, de um método ou de uma propriedade. Isso permite que a classe seja mais flexível e reutilizável, pois as dependências podem ser facilmente substituídas ou modificadas sem afetar a classe.

A injeção de dependência é frequentemente usada em conjunto com outros padrões de projeto, como o padrão de fábrica, o padrão de adaptador e o padrão de estratégia. É amplamente utilizada em frameworks de desenvolvimento de software e em tecnologias como Spring e AngularJS.

Suponhamosw que temos uma classe "UserService" que precisa de uma instância da classe "UserRepository" para acessar um banco de dados e executar operações relacionadas a usuários. Em vez de criar uma nova instância do "UserRepository" dentro da classe "UserService", podemos injetá-la no construtor da seguinte forma:

```java 
public class UserService { 
private UserRepository userRepository;

public UserService(UserRepository userRepository) {     this.userRepository = userRepository;												} // Métodos que utilizam o userRepository para executar operações relacionadas a usuários
}
```

Dessa forma, quando criamos uma nova instância da classe "UserService", precisamos passar uma instância do "UserRepository" no construtor:

```java
UserRepository userRepository = new UserRepositoryImpl(); UserService userService = new UserService(userRepository);`
```

Isso permite que a classe "UserService" seja facilmente testada e reutilizada, pois podemos criar diferentes implementações do "UserRepository" e injetá-las na classe sem precisar modificar o código da classe. Por exemplo, podemos criar uma implementação de teste do "UserRepository" que retorna dados fictícios em vez de acessar um banco de dados real.
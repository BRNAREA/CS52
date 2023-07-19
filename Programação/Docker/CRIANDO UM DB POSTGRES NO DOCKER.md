Certo! Vamos começar do zero então. Aqui está um passo a passo para você criar um container Docker com PostgreSQL e criar uma tabela `users` com as colunas `id`, `name`, `email` e `created_at`:

1.  Certifique-se de ter o Docker instalado em sua máquina. Você pode verificar digitando `docker -v` no terminal.
    
2.  Crie uma nova pasta em sua máquina onde você irá armazenar os arquivos necessários para executar o container. Você pode chamá-la de "postgres" ou qualquer outra coisa que preferir.
    
3.  Abra o terminal e navegue até a pasta criada anteriormente.
    
4.  Digite o seguinte comando para baixar e executar o container do PostgreSQL:
    


`docker run --name postgres-db -e POSTGRES_PASSWORD=minha_senha -p 5432:5432 -d postgres`

Este comando cria um novo container com o nome "postgres-db", define a senha para o usuário "postgres" como "minha_senha" e publica a porta padrão do PostgreSQL (5432). O parâmetro `-d` executa o container em segundo plano.

5.  Verifique se o container está em execução digitando o comando `docker ps`. O resultado deve ser semelhante a este:

bashCopy code

`CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                       NAMES b6d28b986c16   postgres "docker-entrypoint.s…"   10 seconds ago   Up 9 seconds    0.0.0.0:5432->5432/tcp, :::5432->5432/tcp   postgres-db`

6.  Abra um novo terminal e execute o seguinte comando para se conectar ao container do PostgreSQL:


`docker exec -it postgres-db psql -U postgres`

Este comando abre o shell `psql` dentro do container do PostgreSQL e conecta você como o usuário `postgres`.

7.  Execute o seguinte comando SQL para criar a tabela `users` com as colunas `id`, `name`, `email` e `created_at`:


`CREATE TABLE users (     id SERIAL PRIMARY KEY,     name VARCHAR(50) NOT NULL,     email VARCHAR(50) NOT NULL,     created_at TIMESTAMP NOT NULL DEFAULT NOW() );`

Este comando SQL cria uma tabela `users` com uma coluna `id` que se autoincrementa, colunas `name` e `email` do tipo VARCHAR e uma coluna `created_at` do tipo TIMESTAMP com valor padrão `NOW()`.

8.  Verifique se a tabela `users` foi criada corretamente digitando o comando `\dt`. O resultado deve ser semelhante a este:

        `List of relations  Schema | Name  | Type  | Owner --------+-------+-------+-------  public | users | table | postgres (1 row)`

E pronto! Agora você tem um container do PostgreSQL em execução e uma tabela `users` criada nele. A tabela `users` permanecerá salva mesmo se você desligar o container. Você pode sempre reiniciar o container usando o comando `docker start postgres-db`.
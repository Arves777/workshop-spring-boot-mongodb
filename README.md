# Projeto: API REST com Spring Boot e MongoDB

## Descrição
Este projeto consiste em uma API REST desenvolvida com Spring Boot, utilizando MongoDB como banco de dados NoSQL. O objetivo é explorar as principais diferenças entre o paradigma orientado a documentos e o modelo relacional, implementar operações de CRUD e realizar consultas eficientes com Spring Data.

## Tecnologias Utilizadas
- Java 8+
- Spring Boot
- Spring Data MongoDB
- MongoDB
- Maven

## Instalação e Configuração

### Requisitos
Antes de executar o projeto, certifique-se de ter instalado:
- JDK 8+
- Maven
- MongoDB

### Configuração do MongoDB
#### Windows:
1. Baixe e instale o MongoDB Community Server em [mongodb.com](https://www.mongodb.com/)
2. Crie a pasta `C:\data\db`
3. Adicione `C:\Program Files\MongoDB\Server\<versão>\bin` ao PATH
4. Execute `mongod` para iniciar o servidor

#### Mac:
1. Instale o Homebrew (`brew.sh`)
2. Instale o MongoDB com `brew install mongodb`
3. Crie a pasta `/data/db`: `sudo mkdir -p /data/db`
4. Defina as permissões: `sudo chown -Rv $(whoami) /data/db`
5. Execute `mongod` para iniciar o servidor

### Configuração do Projeto
1. Clone o repositório:
   ```sh
   git clone <URL_DO_REPOSITORIO>
   ```
2. Acesse a pasta do projeto:
   ```sh
   cd projeto-spring-mongo
   ```
3. Compile e execute o projeto:
   ```sh
   mvn spring-boot:run
   ```

O servidor estará rodando em `http://localhost:8080`.

## Estrutura do Projeto
```
projeto-spring-mongo/
│-- src/main/java/
│   ├── domain/          # Classes de domínio (User, Post)
│   ├── dto/             # Data Transfer Objects (UserDTO, CommentDTO)
│   ├── repository/      # Interfaces de acesso ao MongoDB (UserRepository, PostRepository)
│   ├── services/        # Regras de negócio (UserService, PostService)
│   ├── resources/       # Controllers REST (UserResource, PostResource)
│   ├── config/          # Configuração inicial do banco de dados (Instantiation)
│-- src/main/resources/
│   ├── application.properties  # Configurações do MongoDB
│-- pom.xml            # Dependências do projeto
```

## Endpoints
### Usuários (`/users`)
- `GET /users` - Retorna todos os usuários
- `GET /users/{id}` - Retorna um usuário por ID
- `POST /users` - Insere um novo usuário
- `DELETE /users/{id}` - Remove um usuário
- `PUT /users/{id}` - Atualiza um usuário

### Posts (`/posts`)
- `GET /posts/{id}` - Retorna um post por ID
- `GET /posts?title=<query>` - Busca posts por título

## Exemplos de Dados
### Usuário
```json
{
  "id": "1001",
  "name": "Maria Brown",
  "email": "maria@gmail.com",
  "posts": ["5001", "5010"]
}
```

### Post
```json
{
  "id": "5001",
  "date": "2024-03-21",
  "title": "Partiu viagem",
  "body": "Vou viajar para São Paulo. Abraços!",
  "author": {
    "id": "1001",
    "name": "Maria Brown"
  },
  "comments": [
    {
      "text": "Boa viagem!",
      "date": "2024-03-21",
      "author": {
        "id": "1013",
        "name": "Alex Green"
      }
    }
  ]
}
```

## Autor
Desenvolvido por Adrian Rosselis com orientações do curso de Java do professor Nélio Alves.

## Licença
Este projeto está licenciado sob a [MIT License](LICENSE).

# Tarefa realizada na disciplina de Engenharia de Software, ministrada pelo Prof. Dr. Eduardo de Lucena Falcão
# Discentes: 
- [Ramylla Barbalho](https://github.com/ramyllaluiza)
- [João Rafael](https://github.com/rafaelsnr)
- Lucas Garcia 

# 🚀 API Rest Sistema de Doações com Docker

API REST para gerenciamento de doações de roupas para ONG's/instituições. O projeto utiliza **Node.js** com **Express** para a API e **JWT** para autenticação. O banco de dados é em memória.
---

- [Histórias de usuário](https://drive.google.com/file/d/1hvcBZ9otv8CZcAHx31syiYaKqbGRsohh/view?usp=sharing)
- [Diagramas UML](https://drive.google.com/file/d/12nYoiyIP6Vxp97JP2ibRe-ra-tdk5TBL/view?usp=sharing)

---

## 🛠 Tecnologias Utilizadas

- **Node.js**: Ambiente de execução JavaScript no lado do servidor.
- **Express**: Framework para criação da API.
- **JWT (JSON Web Token)**: Sistema de autenticação seguro para APIs.
- **Docker**: Plataforma para criação, envio e execução de contêineres.
- **Docker Compose**: Ferramenta para orquestrar contêineres Docker, facilitando a configuração e o gerenciamento.
- **Banco de Dados em Memória**: Dados armazenados temporariamente na memória do servidor.

---

## ⚙️ Funcionalidades

- **Login de usuários**: Permite que doadores e instituições se cadastrem.
- **Registro de doações**: Doadores podem registrar novas doações.
- **Autenticação JWT**: Apenas usuários autenticados podem acessar os endpoints protegidos.

---

## 📝 Como Rodar o Projeto

### 1. Clone o repositório

```bash
git clone https://github.com/ramyllaluiza/APIRest-sistema_doacoes.git
```
### 2. Navegue até o diretório do projeto

```bash
cd APIRest-sistema_doacoes
```
### 3. Requisitos
Antes de rodar o projeto, verifique se o Docker e o Docker Compose estão instalados.

### 4. Instale as dependências

```bash
npm install
```

### 5. Build e Início com Docker

```bash
docker-compose up --build
ou
sudo docker-compose up --build
```

### 6. Acessar a API
A API estará disponível em:

http://localhost:8080

A documentação de demostração foi gerada no Swagger, no link: http://localhost:8080/api-docs
ou no terminal

### 7. Parar os Contêineres
Quando terminar, você pode parar os contêineres com o comando:

```bash
docker-compose down
```
### 🔐 Autenticação JWT
A API utiliza JSON Web Tokens (JWT) para autenticação de usuários. Após o login, o usuário receberá um token JWT, que deve ser incluído no cabeçalho de autorização de todas as requisições subsequentes a endpoints protegidos.

## 1. Endpoint da API (auth)

Este endpoint autentica um usuário (doador, instituição ou administrador) e retorna um token JWT.
Para testar o endpoint, utilizaremos o comando cURL para realizar as requisições.

## Passo a Passo:
- Abra um novo terminal.
- Execute o seguinte comando:

Endpoint: POST /auth/login
- Descrição: Realiza o login de um usuário e retorna um token JWT.

```bash
curl -X POST http://localhost:8080/auth/login \
     -H "Content-Type: application/json" \
     -d '{"email": "joao@example.com", "senha": "123456"}'
```
- Resposta caso bem sucedido:
```bash
{
  "msg": "Autenticação realizada com sucesso!",
  "token": "<Token_Gerado>"
{
```
- Caso não:
```bash
{
  "msg": "Usuário não encontrado!"
}
{
  "msg": "Senha incorreta!"
}
```
Endpoint: GET /auth/perfil
- Descrição: Retorna as informações do perfil do usuário autenticado.
```bash
curl -X GET http://localhost:8080/auth/perfil \
     -H "Authorization: Bearer <COPIE_O_TOKEN_AQUI>" \
     -H "Content-Type: application/json"
```
- Resposta caso bem sucedido:
```bash
{
  "usuario": {
    "id": 1,
    "nome": "João Silva",
    "email": "joao@example.com",
    "iat": 1733781038,
    "exp": 1733784638
  }
}
```
- Caso contrário:
```bash
{
  "msg": "Token inválido!"
}
```
## 2. Endpoint da API (doações)

Esta API permite gerenciar doações realizadas no sistema, incluindo a listagem, criação, atualização e remoção de doações. 

# GET
```bash
curl -X GET http://localhost:8080/doacoes
```
- Resposta: 
  "doacoes": []

# POST:
```bash
curl -X POST http://localhost:8080/doacoes \
     -H "Content-Type: application/json" \
     -d '{
           "nome": "Calça",
           "gênero": "feminino",
           "quantidade": "1"
         }'
```
- Resposta(200): {"msg": "Doação adicionada com sucesso!"}
- Resposta(400): {"msg": "Doação não encontra"}
### Faça o GET novamente para obter o ID

## PUT:
  ```bash
curl -X PUT "http://localhost:8080/doacoes?id=<ID>" \
     -H "Content-Type: application/json" \
     -d '{
           "nome": "Calça preta",
           "gênero": "feminino",
           "quantidade": "1"}'
  ```
- Resposta(200): {"msg": "Doação atualizada com sucesso!"}
- Resposta(400): {"msg": "Doação não encontrada!"}
## DELETE:
  ```bash
curl -X DELETE "http://localhost:8080/doacoes?id=<ID>"
  ```
- Resposta(200): {"msg": "Doação deletada com sucesso!"}
- Resposta(400): {"msg": "Doação não encontrada!"}

## 3. Endpoint da API (login)

A API de Login permite gerenciar autenticações e contas de usuários no sistema. Com ela, é possível consultar, criar, atualizar e excluir logins.  

# GET
```bash
curl -X GET http://localhost:8080/login
```
- Resposta(200): {"logins": []}

# POST:
```bash
curl -X POST http://localhost:8080/login \
     -H "Content-Type: application/json" \
     -d '{
           "email": "luizalber@gmail.com",
           "senha": "senhaliuzadx"
         }'
```
- Resposta(200): {
  "msg": "Login registrado com sucesso!",
  "login": {
    "id": "ae0d2570-692f-4bdc-b78d-9e47a6ce342c",
    "email": "luizalber@gmail.com",
    "senha": "$2b$10$MthKY6wBo.uDwWWYOcvNuu27oRbV67uyW/j5yB6Nhp6trPDi..pnC"
  }
}
- Resposta(400): { msg: "Login não encontrado!" }
  
### Faça o GET novamente para obter o ID

## PUT:
  ```bash
curl -X PUT "http://localhost:8080/login?id=<ID>" \
     -H "Content-Type: application/json" \
     -d '{
           "email": "pedroluiza@gmail.com",
           "senha": "123456"
         }'
  ```
- Resposta(200): {"msg": "Usuário atualizado com sucesso!"}
- Resposta(400): {"msg": "Usuário não encontrado!"}
## DELETE:
  ```bash
curl -X DELETE "http://localhost:8080/login?id=<ID>"
  ```
- Resposta(200): {"msg": "Login deletado com sucesso!"}
- Resposta(400): {"msg": "Login não encontrado!"}

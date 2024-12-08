# 🚀 API Rest Sistema de Doações com Docker

API REST para gerenciamento de doações de alimentos e outros itens. O projeto utiliza **Node.js** com **Express** para a API e **JWT** para autenticação. O banco de dados é em memória.

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

### 7. Parar os Contêineres
Quando terminar, você pode parar os contêineres com o comando:

```bash
docker-compose down
```
🔐 Autenticação JWT
A API utiliza JSON Web Tokens (JWT) para autenticação de usuários. Após o login, o usuário receberá um token JWT, que deve ser incluído no cabeçalho de autorização de todas as requisições subsequentes a endpoints protegidos.

1. Endpoint da API
Este endpoint autentica um usuário (doador, instituição ou administrador) e retorna um token JWT.

Endpoint: POST /auth/login
- Descrição: Realiza o login de um usuário e retorna um token JWT.
```bash
### Corpo da requisição: 
{
  "email": "joao@example.com",
  "senha": "123456"
}
### Exemplo de requisição:
POST http://localhost:8080/auth/login
Content-type: application/json
### Resposta caso bem sucedido:
{
  "msg": "Autenticação realizada com sucesso!",
  "token": "TOKEN_GERADO"
}
### Caso contrário:
{
  "msg": "Usuário não encontrado!"
}
```

Endpoint: GET /auth/perfil
- Descrição: Retorna as informações do perfil do usuário autenticado.
```bash
### Corpo da requisição: 
GET http://localhost:8080/auth/perfil
Authorization: Bearer "TOKEN_GERADO"
### Resposta cado bem sucedido:
  "usuario":
{
    "id": 1,
    "nome": "João Silva",
    "email": "joao@example.com",
    "iat": 1733667255,
    "exp": 1733670855
  }
### Caso contrário:
{
  "msg": "Token inválido!"
}
```

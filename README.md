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
Clone este repositório para sua máquina local utilizando o comando:

```bash
git clone https://github.com/ramyllaluiza/APIRest-sistema_doacoes.git
```
### 2. Navegue até o diretório do projeto
Clone este repositório para sua máquina local utilizando o comando:

```bash
cd APIRest-sistema_doacoes
```
### 3. Requisitos
Antes de rodar o projeto, verifique se o Docker e o Docker Compose estão instalados.

### 4. Instale as dependências
Clone este repositório para sua máquina local utilizando o comando:

```bash
npm install
```

### 5. Build e Início com Docker
Clone este repositório para sua máquina local utilizando o comando:

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

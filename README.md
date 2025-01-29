# API RESTful de Usuários - Laravel

## Visão Geral
Esta API permite criar, listar, atualizar e deletar usuários armazenados em um banco de dados MySQL. Todas as respostas são fornecidas no formato JSON.

## Tecnologias Utilizadas
- Laravel 10
- MySQL
- PHP 8+
- Composer

## Configuração do Projeto

### 1. Clonar o Repositório
```bash
git clone https://github.com/wnode/user-api.git
cd nome-do-repositorio
```

### 2. Instalar Dependências
```bash
composer install
```

### 3. Configurar o Banco de Dados
Edite o arquivo `.env` e configure as credenciais do banco:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=user_api
DB_USERNAME=root
DB_PASSWORD=senha
```

### 4. Criar a Estrutura do Banco
```bash
php artisan migrate
```

### 5. Rodar a API
```bash
php artisan serve
```

A API estará acessível em `http://127.0.0.1:8000`

## Endpoints

### Listar Todos os Usuários
**GET** `/api/users`
#### Resposta de Sucesso (200):
```json
[
  {
    "id": 1,
    "name": "Allan",
    "email": "allan@email.com",
    "created_at": "2024-01-01T12:00:00Z"
  }
]
```

---
### Criar um Novo Usuário
**POST** `/api/users`
#### Corpo da Requisição:
```json
{
  "name": "Allan",
  "email": "allan@email.com",
  "password": "123456"
}
```
#### Resposta de Sucesso (201):
```json
{
  "id": 1,
  "name": "Allan",
  "email": "allan@email.com",
  "created_at": "2024-01-01T12:00:00Z"
}
```

---
### Obter Detalhes de um Usuário
**GET** `/api/users/{id}`
#### Resposta de Sucesso (200):
```json
{
  "id": 1,
  "name": "Allan",
  "email": "allan@email.com",
  "created_at": "2024-01-01T12:00:00Z"
}
```
#### Erro (404):
```json
{ "message": "Usuário não encontrado" }
```

---
### Atualizar um Usuário
**PUT** `/api/users/{id}`
#### Corpo da Requisição:
```json
{
  "name": "Allan Souza"
}
```
#### Resposta de Sucesso (200):
```json
{
  "id": 1,
  "name": "Allan Souza",
  "email": "allan@email.com",
  "updated_at": "2024-01-01T12:30:00Z"
}
```
#### Erro (404):
```json
{ "message": "Usuário não encontrado" }
```

---
### Deletar um Usuário
**DELETE** `/api/users/{id}`
#### Resposta de Sucesso (200):
```json
{ "message": "Usuário excluído com sucesso" }
```
#### Erro (404):
```json
{ "message": "Usuário não encontrado" }
```

## Validação e Tratamento de Erros
- **422 Unprocessable Entity:** Erros de validação.
- **404 Not Found:** Usuário não encontrado.


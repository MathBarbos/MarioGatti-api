# MarioGatti-api
# Sistema de Gerenciamento de Pacientes

Um sistema simples de **gerenciamento de pacientes** desenvolvido em **Laravel 10**, com **API RESTful** para criar, listar, atualizar, visualizar e deletar pacientes do banco de dados.

## Estrutura do Projeto

* `app/Models/Patient.php` → Model do paciente
* `app/Http/Controllers/PatientController.php` → Controller da API
* `routes/api.php` → Rotas da API
* `database/migrations` → Migrations do banco de dados
* `.env` → Configurações de banco
* `README.md` → Este arquivo explicativo

## README.md

Segue o conteúdo completo do README pronto para uso:

````markdown
# Sistema de Gerenciamento de Pacientes

Um sistema simples de **gerenciamento de pacientes** desenvolvido em **Laravel 10**, com **API RESTful** para criar, listar, atualizar, visualizar e deletar pacientes do banco de dados.  

O sistema utiliza a **model `Patient`** para interagir com o banco e fornece respostas em **JSON** para todas as operações.

---

## Funcionalidades

O `PatientController` oferece os seguintes endpoints:

| Método HTTP | Rota                 | Descrição                                    |
|-------------|---------------------|----------------------------------------------|
| GET         | `/api/patients`         | Lista todos os pacientes com paginação       |
| POST        | `/api/patients`         | Cria um novo paciente                        |
| GET         | `/api/patients/{id}`    | Mostra os detalhes de um paciente específico |
| PUT/PATCH   | `/api/patients/{id}`    | Atualiza os dados de um paciente            |
| DELETE      | `/api/patients/{id}`    | Deleta um paciente                           |

### Estrutura de um paciente

Cada paciente possui os seguintes campos:

- `id` (inteiro) – Identificador único
- `name` (string) – Nome do paciente
- `birthday` (date) – Data de nascimento
- `cpf` (string) – CPF do paciente
- `rg` (string, opcional) – RG do paciente

---

## Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- PHP >= 8.1
- Composer
- Banco de dados PostgreSQL
- Laravel 12

---

## Instalação

1. Clone o repositório:

```bash
git clone <url-do-repo>
cd nome-do-projeto
````

2. Instale as dependências do Laravel:

```bash
composer install
```

3. Configure o `.env` para conexão com o banco de dados:

```dotenv
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nome_do_banco
DB_USERNAME=usuario
DB_PASSWORD=senha
```

4. Crie a tabela `patients` usando migrations:

```bash
php artisan migrate
```

---

## Configuração das Rotas

```
> O `apiResource` já cria todas as rotas RESTful automaticamente: `index`, `store`, `show`, `update` e `destroy`.

---

## Testando a API

Você pode usar o **Postman**, **Insomnia** ou qualquer cliente HTTP.

### Criar paciente (POST `/api/patients`)

```json
{
    "name": "João Silva",
    "birthday": "1990-05-12",
    "cpf": "123.456.789-00",
    "rg": "12.345.678-9"
}
```

### Listar pacientes (GET `/api/patients`)

Resposta:

```json
{
    "message": "Pacientes listados com sucesso",
    "data": [
        {
            "id": 1,
            "name": "João Silva",
            "birthday": "1990-05-12",
            "cpf": "123.456.789-00",
            "rg": "12.345.678-9"
        }
    ]
}
```

### Atualizar paciente (PUT `/api/patients/{id}`)

```json
{
    "name": "João da Silva",
    "birthday": "1990-05-12",
    "cpf": "123.456.789-00",
    "rg": "12.345.678-9"
}
```

### Deletar paciente (DELETE `/api/patients/{id}`)

Resposta:

```json
{
    "message": "Paciente deletado com sucesso"
}
```

---

## Validação de Dados

O método `validateRequest` garante que:

* `name` seja obrigatório e texto
* `birthday` seja obrigatório e data válida
* `cpf` seja obrigatório e texto
* `rg` seja opcional e texto

Se houver algum erro de validação, a API retorna **422** com detalhes.

---

## Tratamento de Erros

O sistema trata diferentes tipos de erros:

* **Paciente não encontrado** → 404
* **Erro de validação** → 422
* **Erro inesperado no servidor** → 500

Isso garante respostas consistentes para o frontend.

---

## Autor

Matheus Santos

```
```

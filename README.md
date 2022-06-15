# Desafio 01 - Conceitos do Node.js

## :computer: Sobre o desafio

<hr>

Nesse desafio, você deverá criar uma aplicação para treinar o que aprendeu até agora no Node.js!

Essa será uma aplicação para gerenciar tarefas (em inglês _todos_). Será permitida a criação de um usuário com `name` e `username`, bem como fazer o CRUD de *todos*:

- Criar um novo _todo_;
- Listar todos os _todos_;
- Alterar o `title` e `deadline` de um _todo_ existente;
- Marcar um _todo_ como feito;
- Excluir um _todo_;

Tudo isso para cada usuário em específico (o `username` será passado pelo header) 🚀

## :rocket: Techs

<ul>
  <li> Javascript </li>
  <li> Node.js </li>
  <li> Express </li>
  <li> uuid </li>
  <li> cors </li>
</ul>

## Desenvolvimento

---

### Pré-requisitos

- Instalar [Node.js](https://nodejs.org)

- Instalar [Yarn](https://yarnpkg.com/)

### Clone o repositório

```bash
$ git clone https://github.com/vitorgaletti/ignite-nodejs-conceitos-do-nodejs.git
```

### Executar Projeto

```bash
# Mudar para directório
$ cd ignite-nodejs-conceitos-do-nodejs/
```

- Instalar dependências

```bash
$ yarn install
```

- Execute

```bash
$ yarn dev
```

- Executar scripts

|        Ação        | Utilização  |
| :----------------: | :---------: |
| Iniciar o servidor | `yarn dev`  |
|  Executar testes   | `yarn test` |

URL da API = http://localhost:3333

<br>

## API Reference

#### Cadastrar novo usuário

```http
POST /users
```

| Request Field | Type     |
| :------------ | :------- |
| `name`        | `string` |
| `username`    | `string` |

| Status code | Description                         |
| :---------- | :---------------------------------- |
| `201`       | Conta criada com sucesso            |
| `400`       | Já possui um usuário com mesmo nome |

```json
{
  "id": "71200838-f874-4285-a6d8-0d100bcc5eee",
  "name": "vitor",
  "username": "vitor1997",
  "todos": []
}
```

#### Visualizar tarefas a fazer

```http
GET /todos
```

| Header Field |   Type   | Description                                         |
| :----------- | :------: | --------------------------------------------------- |
| `username`   | `string` | Informar o username do usuário cadastrado no header |

| Response Field | Type      | Description                      |
| :------------- | :-------- | :------------------------------- |
| `id`           | `number`  | Identificador da tarefa          |
| `title`        | `string`  | Título da tarefa                 |
| `done`         | `boolean` | A tarefa foi feita ou não        |
| `deadline`     | `string`  | Data limite da entrega da tarefa |
| `created_at`   | `string`  | Data criada da tarefa            |

| Status code | Description                                      |
| :---------- | :----------------------------------------------- |
| `200`       | Visualizar todas as tarefa do username informado |
| `404`       | Usuário não encontrado                           |

```json
[
  {
    "id": "b73cae2b-7c0b-4de0-8285-8db0a609327e",
    "title": "Estudar Matematica",
    "done": false,
    "deadline": "2022-06-10T00:00:00.000Z",
    "created_at": "2022-06-15T21:17:44.881Z"
  }
]
```

#### Criar uma tarefa

```http
POST /todos
```

| Request Field | Type     | Description                      |
| :------------ | :------- | :------------------------------- |
| `title`       | `string` | Título da tarefa                 |
| `deadline`    | `string` | Data limite da entrega da tarefa |

| Header Field | Type     | Description                                         |
| :----------- | :------- | :-------------------------------------------------- |
| `username`   | `string` | Informar o username do usuário cadastrado no header |

| Status code | Description               |
| :---------- | :------------------------ |
| `201`       | Tarefa criada com sucesso |
| `404`       | Usuário não encontrado    |

```json
{
  "title": "Estudar Matematica",
  "deadline": "2022-06-10"
}
```

#### Alterar uma tarefa

```http
PUT /todos/:id
```

| Parameter | Type     | Description             |
| :-------- | :------- | :---------------------- |
| `id`      | `number` | Identificador da tarefa |

| Request Field | Type     | Description                      |
| :------------ | :------- | :------------------------------- |
| `title`       | `string` | Título da tarefa                 |
| `deadline`    | `string` | Data limite da entrega da tarefa |

| Header Field |   Type   | Description                                         |
| :----------- | :------: | --------------------------------------------------- |
| `username`   | `string` | Informar o username do usuário cadastrado no header |

| Status code | Description                 |
| :---------- | :-------------------------- |
| `200`       | Tarefa alterada com sucesso |
| `404`       | Usuário não encontrado      |
| `404`       | Tarefa não encontrada       |

```json
{
  "title": "Tarefa Portugues",
  "deadline": "2022-06-26"
}
```

#### Alterar status da tarefa para feita

```http
PATCH /todos/:id/done
```

| Parameter | Type     | Description             |
| :-------- | :------- | :---------------------- |
| `id`      | `number` | Identificador da tarefa |

| Header Field |   Type   | Description                                         |
| :----------- | :------: | --------------------------------------------------- |
| `username`   | `string` | Informar o username do usuário cadastrado no header |

| Status code | Description                 |
| :---------- | :-------------------------- |
| `200`       | Tarefa alterada com sucesso |
| `404`       | Usuário não encontrado      |
| `404`       | Tarefa não encontrada       |

```json
{
  "id": "8d7b647f-118f-487a-be3f-3c680f82a68d",
  "title": "Estudar Matematica",
  "done": true,
  "deadline": "2022-06-10T00:00:00.000Z",
  "created_at": "2022-06-15T21:31:31.925Z"
}
```

#### Excluir uma tarefa

```http
DELETE /todos/:id
```

| Parameter | Type     | Description             |
| :-------- | :------- | :---------------------- |
| `id`      | `number` | Identificador da tarefa |

| Header Field |   Type   | Description                                         |
| :----------- | :------: | --------------------------------------------------- |
| `username`   | `string` | Informar o username do usuário cadastrado no header |

| Status code | Description                 |
| :---------- | :-------------------------- |
| `204`       | Tarefa alterada com sucesso |
| `404`       | Usuário não encontrado      |
| `404`       | Tarefa não encontrada       |

## Autor

- [@vitorgaletti](https://github.com/vitorgaletti)

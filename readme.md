# Todo API Documentation

This documentation provides information about the API endpoints and how to use them to interact with a simple Todo application. The API is designed to manage a list of Todos, and it includes various features like filtering, sorting, and pagination.

## Table of Contents

- [Introduction](#introduction)
- [Endpoints](#endpoints)
  - [Get All Todos](#get-all-todos)
  - [Get Todo by ID](#get-todo-by-id)
  - [Create Todo](#create-todo)
  - [Update Todo](#update-todo)
  - [Remove Todo](#remove-todo)

---

## Introduction

This API allows you to manage a list of Todos. Each Todo has the following properties:

- `id` (string): A unique identifier for the Todo.
- `task` (string): The description of the task to be done.
- `status` (boolean): The status of the task (true for completed, false for not completed).
- `date` (string): The date when the task was created or due.

## Endpoints

### Get All Todos

#### Endpoint: `GET /api/todos`

- **Description**: Retrieve a list of all Todos.

##### Query Parameters

- `task` (string, optional): Filter Todos by task description.
- `status` (string, optional): Filter Todos by status (`true` for completed, `false` for not completed).
- `sort` (string, optional): Sort Todos by task description (use `sort=task` for ascending order, `sort=-task` for descending order).
- `page` (number, optional): Paginate the result set by specifying the page number.
- `limit` (number, optional): Set the maximum number of Todos per page.

##### Example Request

```http
GET /api/todos?task=Buy&status=true&sort=task&page=1&limit=10
```

##### Example Response

```json
{
  "total": 2,
  "todos": [
    {
      "id": "1a2b3c4d",
      "task": "Buy groceries",
      "status": true,
      "date": "2023-09-06"
    },
    {
      "id": "5e6f7g8h",
      "task": "Buy gifts",
      "status": true,
      "date": "2023-09-07"
    }
  ]
}
```

### Get Todo by ID

**Endpoint**: `GET /api/todos/:id`

- **Description**: Retrieve a specific Todo by its ID.

##### Example Request

```
http GET /api/todos/1a2b3c4d
```

##### Example Response

```json
{
  "id": "1a2b3c4d",
  "task": "Buy groceries",
  "status": true,
  "date": "2023-09-06"
}
```

### Create Todo

**Endpoint**: `POST /api/todos`

- **Description**: Create a new Todo.
- **Request Body**:
  - `task` (string, required): The description of the task.
  - `status` (boolean, required): The status of the task (true for completed, false for not completed).
  - `date` (string, optional): The date when the task was created or due.

##### Example Request

```
POST /api/todos
Content-Type: application/json

{
    "task": "Clean the house",
    "status": false,
    "date": "2023-09-08"
}
```

##### Example Response

```json
{
  "id": "9i8h7g6f",
  "task": "Clean the house",
  "status": false,
  "date": "2023-09-08"
}
```

### Update Todo

**Endpoint**: `PUT /api/todos/:id`

- **Description**: Update an existing Todo by its ID.
- **Request Body**:
  - `task` (string, required): The updated description of the task.
  - `status` (boolean, required): The updated status of the task.
  - `date` (string, optional): The updated date of the task.

```
PUT /api/todos/9i8h7g6f
Content-Type: application/json

{
    "task": "Clean the house (updated)",
    "status": true,
    "date": "2023-09-09"
}
```

##### Example Response

```json
{
  "id": "9i8h7g6f",
  "task": "Clean the house (updated)",
  "status": true,
  "date": "2023-09-09"
}
```

### Remove Todo

**Endpoint**: `DELETE /api/todos/:id`

- **Description**: Remove a specific Todo by its ID.

```
DELETE /api/todos/9i8h7g6f
```

##### Example Response

```json
no content
```

---

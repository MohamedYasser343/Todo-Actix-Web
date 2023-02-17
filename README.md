# Todo-Actix-Web
in this project I test rust and actix web high performance.

---

# Table Of Content
This repo consists of:
1. database.sql (database code)
2. cargo.toml (include dependencies for the project)
2. env.env (include server and database information)
3. src dir (include rust codes)

---

# How To Install

install the project:

```
git clone https://github.com/MohamedYasser343/Todo-Actix-Web.git
```

---

## Usage
```
# Copy .env file
cp env.env .env
# Run postgres
docker-compose up -d postgres
# Install diesel
cargo install diesel_cli --no-default-features --features postgres
# Run db migrations
DATABASE_URL=postgres://actix:actix@localhost:5432/actix diesel migration run
# Run unit tests
cargo test
# Run integration tests
cargo test --features "integration"
# Run the server (Add --release for an optimized build)
cargo run 
```
```
curl -s http://<host>:<port>/todos
```

---

# How To Run


1. config your server and database information in **.env**:

2. use **Postman** or **curl** for using the project
3. you can send:
  * get req
  * post req
  * put req
  * ~~delete req~~
  
4. in my opinion actix web is really fast and you can check it using:

```
ab -n <number of req you want (for example: 100000)> -k -c 30 -q http://<host>:<port>/todos
```

---

# Routes

- `GET` `/` -> Status

  **Response:**
  ```
  {
    "status": "Up"
  }
  ```

- `GET` `/todos` -> Get todo lists

  **Response:**
  ```
  [
    {
      "id": 1,
      "title": "Grocery list"
    },
    ...
  [
  ```
- `GET` `/todos/1` -> Get single todo list

  **Response:**
  ```
  {
    "id": 1,
    "title": "Grocery list"
  }
  ```
- `POST` `/todos` -> Create todo list

  **Request Header:**
  ```
  Content-Type: application/json
  ```
  **Request Body:**
  ```
  {
    "title": "List title"    
  }
  ```
  **Response:**
  ```
  {
    "id": 1,
    "title": "Grocery list"
  }
  ```
- `GET` `/todos/1/items` -> Get items of the todo list

  **Response:**
  ```
  [
    {
      "id": 1,
      "list_id": 1,
      "title": "Milk",
      "checked": true
    },
    {
      "id": 1,
      "list_id": 2,
      "title": "Bread",
      "checked": false
    }
  ]
  ```
- `GET` `/todos/1/items/1` -> Get single item of the todo list

  **Response:**
  ```
  {
    "id": 1,
    "list_id": 1,
    "title": "Milk",
    "checked": true
  }
  ```

- `POST` `/todos/1/items` -> Create todo list item

  **Request Header:**
  ```
  Content-Type: application/json
  ```
  **Request Body:**
  ```
  {
    "title": "Eggs"    
  }
  ```
  **Response:**
  ```
  {
    "id": 1,
    "list_id": 1,
    "title": "Eggs",
    "checked": false
  }
  ```
- `PUT` `/todos/1/items/1` -> Check todo

  **Response:**
  ```
  {
    "result": true
  }
  ```
  Result:
  - `true` -> Checked
  - `false` -> Already checked. Nothing to do.

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

# How To Run


1. config your server and database information in **env.env**:

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

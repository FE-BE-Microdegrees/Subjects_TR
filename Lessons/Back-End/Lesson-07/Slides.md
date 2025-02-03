---
marp: true
---

# Web Development

## Back-End Development


---

## Today's Topics

- Review of the previous lecture
- [Connecting a Database to NodeJS](../../../Subjects/Databases/Topics/MySQL-NodeJS/README.md)
- Database Queries in a Node API

---

## What Did We Discuss Last Time?

---

## Connecting a Database to NodeJS

---

## MySQL with NodeJS

To enable NodeJS to communicate with a MySQL database, we use the `mysql2` module, which allows creating a connection with MySQL, sending queries, and receiving responses.

```bash
npm install mysql2
```

---

## Connecting to the Database

Connecting a database to NodeJS is done using the MySQL module, which allows creating a connection with MySQL, sending queries, and receiving responses.

```javascript
const mysql = require('mysql2');

const pool = mysql.createPool({
  host: 'localhost',
  user: 'mysql-user',
  password: 'mysql-password',
  database: 'mydatabase'
});

const promisePool = pool.promise();

module.exports = promisePool;
```

`Pool`  is a MySQL connection manager that allows creating multiple connections and reusing them.

---

## Database Queries in Services

To perform database queries, we create services that use the database connection to send queries.

```javascript
const db = require('../db');

const getAllUsers = async () => {
  const [rows] = await db.query('SELECT * FROM users');
  return rows;
};
```

---

## SQL-injection

SQL injection is a security attack that allows an attacker to inject malicious SQL code into a web application, manipulating database queries and gaining access to confidential data.
---

## Parameterized Queries

Parameterized queries allow using variables and values in queries, making them dynamic and more secure.

Parameterized queries help prevent SQL injection attacks.

```javascript
const getUserById = async (id) => {
  const [rows] = await db.query('SELECT * FROM users WHERE id = ?', [id]);
  return rows[0];
};

const createUser = async (username, email) => {
  const [result] = await db.query('INSERT INTO users (username, email) VALUES (?, ?)', [username, email]);
  return result.insertId;
};
```

> Note that the query variable is replaced with a question mark  `?` and values are provided in an array.

---

## Updating and Deleting Resources

Database queries allow updating and deleting resources.

```javascript
const updateUser = async (id, username, email) => {
  const [result] = await db.query('UPDATE users SET username = ?, email = ? WHERE id = ?', [username, email, id]);
  return result.affectedRows;
};
```

Alternatively:

```javascript
const updatedUser = async (id, user) => {
  const [result] = await db.query('UPDATE users SET ? WHERE id = ?', [user, id]);
  return result.affectedRows;
};
```

In the last example, `user` must be an object with keys matching the database fields.

---

## Homework

- Add database connection and queries to your application.

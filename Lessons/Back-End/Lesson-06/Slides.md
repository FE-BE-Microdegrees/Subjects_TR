---
marp: true
---

# Web Development

## Back-End Development



---

## Today's Topics

- Review of the previous lecture
- Database
- [Relational Database](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Databases/Topics/Relational-Database/README.md)
- [MySQL](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Databases/Topics/MySQL/README.md)
- [MySQL in Docker](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Databases/Topics/Docker-MySQL/README.md)
- [Making SQL Queries](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Databases/Topics/MySQL-Queries/README.md)
- Creating a Database
- Creating Tables
- Inserting Data
- Making Queries
- Homework

---

## What Did We Discuss Last Time?

---

## What is a Database?

---

## Database

An organized collection of data structured to make it easy to manage, update, and search. Databases allow efficient data storage and access.

---

## Database System

Software that enables the creation, management, and usage of databases. It is known as a Database Management System (**DBMS**).

---

## Relational Database

---

## Relational Database - 1

Relational databases are widely used data management tools that allow data to be stored in a structured and organized format. These databases use a system of tables to store and manage data and are based on the relational model.

---

## Main Components of a Relational Database

- Tables
- Primary Key
- Foreign Key
- Indexes
- ...

---

## Tables

Tables are the basic elements of relational databases, containing rows and columns. Each table represents a specific set of data (e.g., customers, orders, products).

- **Row:** A data record in the table. Each row contains data according to the table's columns. A row may also be referred to as a record or entity.
- **Column:** A table attribute, also called fields.

Example table:

| ID  | Name  | Age |
|-----|-------|-----|
| 1   | John  | 25  |
| 2   | Mary  | 30  |
| 3   | Peter | 22  |

---

## Primary Key

The primary key is a unique identifier that distinguishes each row in a table, ensuring that each record is unique.

---

## Foreign Key

A foreign key is a column or a set of columns that creates a relationship between two or more tables by referencing the primary key in another table.

---

## Indexes

An index is a data structure that allows faster searching and query execution in a table. Indexes are created based on one or more columns and provide references that enable faster retrieval of specific rows from the table.

---

## MySQL

MySQL is an open-source relational database management system (**RDBMS**) widely used in web application development. MySQL uses SQL (Structured Query Language) for data management and queries.

---

## Docker

Docker is an open-source container virtualization platform that allows developers to build, run, and share applications in containers. Docker uses Linux container technology to package an application's code, dependencies, and configuration into a single container.

---

## Docker Containers

Docker containers are isolated, lightweight virtual machines that run on the Docker platform. Each container includes the application code, dependencies, and configuration, packaged as a container image.

---

## Docker Hub

Docker Hub is Docker's official registry platform, enabling developers to find, share, and run Docker containers. Docker Hub includes thousands of public containers for running various applications and services.

---

## MySQL in Docker

During the course, we will use MySQL in a Docker container to create and manage databases in the development environment, as it is a quick and easy way to run and use MySQL without needing to install it directly on our computer.

---

## Running MySQL in Docker

MySQL environment variables:

- `MYSQL_ROOT_PASSWORD`: Password for the MySQL root user.
- `MYSQL_DATABASE`: The name of the database to create.
- `MYSQL_USER`: Database username.
- `MYSQL_PASSWORD`: Database user password.

---

## SQLTools VS Code Extension

SQLTools is a Visual Studio Code extension that allows developers to connect and manage SQL databases directly within the VS Code environment. SQLTools supports various database systems, including MySQL, PostgreSQL, SQLite, SQL Server, and many more.

---

## Creating a Database

To create a database, we use the SQL command `CREATE DATABASE` followed by the database name.

```sql
CREATE DATABASE mydatabase;
```

> When using MySQL in Docker, the database is created during the container startup by setting the `MYSQL_DATABASE`environment variable.

---

## Creating Tables

To create a table, we use the SQL command `CREATE TABLE` followed by the table name and column definitions.

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(50),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## Data Types

MySQL supports various data types that define the type and constraints of column values. Some common data types include:

- `INT`: Integer value.
- `VARCHAR(n)`: Variable-length character string.
- `TEXT`: Long text data.
- `DATE`: Date.
- `DATETIME`: Date and time.
- `TIMESTAMP`: Date and time, updated automatically.
- `BOOLEAN`: Boolean value (TRUE or FALSE).
- ...

> The  `BOOLEAN` data type doesn't actually exist in MySQL; it is treated as `TINYINT(1)` .

---

## Additional Field Properties

Fields can have different properties that define column constraints and behavior. Some common additional field properties are:

- `NOT NULL`: Value cannot be NULL.
- `UNIQUE`: Value must be unique.
- `DEFAULT value`: Default value assigned if no value is specified.
- `AUTO_INCREMENT`: Column value automatically increments with each new row.
- `PRIMARY KEY`: Unique identifier distinguishing each record.
- `FOREIGN KEY`: Foreign key creating relationships between tables.
- ...

---

## Modifying Tables

To modify tables, we use the SQL command `ALTER TABLE`, To modify tables, we use the SQL command.

```sql
ALTER TABLE users ADD COLUMN password VARCHAR(255);
```

To delete a column, we use the `DROP COLUMN` command.

```sql
ALTER TABLE users DROP COLUMN password;
```

---

## Dropping a Table

To delete a table, we use the SQL command `DROP TABLE`, followed by the table name.

```sql
DROP TABLE users;
```

> Be cautious when using the  `DROP` command, as it permanently deletes data and structure.

---

## Relationships

Relationships are used in databases to create associations between two or more tables. Relationships enable efficient data retrieval and management by creating links using foreign keys.
---

## Adding a Foreign Key

To add a foreign key, we use the SQL command `FOREIGN KEY`, followed by the column name and a reference to the primary key in another table.

```sql
CREATE TABLE posts (
    id INT PRIMARY KEY,
    user_id INT,
    title VARCHAR(255),
    content TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

---

## Types of Relationships

- **One-to-One:** Each record in the first table corresponds to exactly one record in the second table.
- **One-to-Many:**  Each record in the first table corresponds to multiple records in the second table.
- **Many-to-Many:** Multiple records in the first table correspond to multiple records in the second table and vice versa.

---

## Inserting Data

To insert data, we use the SQL command `INSERT INTO`, followed by the table name and the values of the columns.

```sql
INSERT INTO users (username, email) VALUES ('alice', 'alice@alice.ee');
```

---

## Making Queries

To read and query data from tables, we use the SQL command `SELECT`, mollowed by the column names or `*` to select all columns.

```sql
SELECT * FROM users;
```

---

## Specific Queries

To refine queries, we use the  `WHERE` clause, which limits the query results according to specified conditions.

```sql
SELECT * FROM users WHERE username = 'alice';
```

```sql
SELECT * FROM users WHERE id = 1;
```

```sql
SELECT * FROM users WHERE age > 18;
```

---

## Specifying Which Data to Display

```sql
SELECT username, email FROM users;
```

```sql
SELECT username, email FROM users WHERE age > 18;
```

---

## Homework

- Create a MySQL database and tables for users, posts, and comments.
- Add data to the tables to make it usable within your API.
- Make queries to retrieve data for users, posts, and comments.

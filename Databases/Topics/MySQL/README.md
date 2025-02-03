# MySQL Basics

MySQL is one of the most popular open-source relational database management systems (RDBMS). It is widely used in web applications and various industries due to its performance, reliability, and ease of use. This chapter provides an overview of MySQL's fundamental components and how to get started with using it.

![MySQL](MySQL.webp)

- [MySQL Basics](#mysql-basics)
  - [Learning Outcomes](#learning-outcomes)
  - [Introduction to MySQL and SQL](#introduction-to-mysql-and-sql)
  - [MySQL Installation and Setup](#mysql-installation-and-setup)
    - [Installing MySQL Server](#installing-mysql-server)
    - [MySQL Workbench](#mysql-workbench)
  - [Creating a Database and Tables](#creating-a-database-and-tables)
    - [Creating a New Database](#creating-a-new-database)
    - [Creating Tables](#creating-tables)
  - [Manipulating Data](#manipulating-data)
    - [Inserting Data](#inserting-data)
    - [Selecting Data](#selecting-data)
    - [Updating Data](#updating-data)
    - [Deleting Data](#deleting-data)
  - [Database Management](#database-management)
    - [Creating Indexes](#creating-indexes)
    - [Creating Views](#creating-views)
  - [Backing Up and Restoring Data](#backing-up-and-restoring-data)
    - [Backing Up Data](#backing-up-data)
    - [Restoring Data](#restoring-data)
  - [Sources](#sources)
  - [Review Questions or Exercises](#review-questions-or-exercises)
  - [Exercise](#exercise)

## Learning Outcomes

By the end of this chapter, learners should be able to:

- Explain what MySQL is and how it differs from other database systems;
- Install and configure MySQL server;
- Use MySQL Workbench to manage databases and tables;
- Create and manage databases and tables in MySQL;
- Perform basic database operations in MySQL.

## Introduction to MySQL and SQL

**MySQL:** MySQL is an open-source relational database management system (RDBMS) widely used for web applications and enterprise data management. It is based on the SQL (Structured Query Language) standard.

**SQL (Structured Query Language):** SQL is the standard query language used to manage and manipulate data in relational databases. It enables the creation, modification, deletion, and querying of data in tables.

## MySQL Installation and Setup

### Installing MySQL Server

MySQL server installation varies based on the operating system. Below are instructions for Windows, macOS, and Linux.

- **Windows:** Use MySQL Installer for Windows.
- **macOS:** Use MySQL DMG Installer.
- **Linux:** Install MySQL using `apt-get` or `yum`.

Example for Windows:

1. Download the MySQL Installer from the [official MySQL website](https://dev.mysql.com/downloads/installer/).
2. Run the installer and select MySQL Server and MySQL Workbench for installation.
3. Follow the on-screen instructions to configure the server and complete the installation.

### MySQL Workbench

MySQL Workbench is a powerful tool for managing and developing MySQL databases. It provides a graphical interface for writing SQL queries, designing databases, and managing databases.

- **Download and install MySQL Workbench** from the [official MySQL website](https://dev.mysql.com/downloads/workbench/).
- **Launch MySQL Workbench** and create a new connection to the MySQL server using the login credentials set during server installation.

## Creating a Database and Tables

### Creating a New Database

To create a database in MySQL, use the `CREATE DATABASE` SQL command.

```sql
CREATE DATABASE my_database;
```

This command creates a new database called `my_database`.

### Creating Tables

To create a table in MySQL, use the `CREATE TABLE` SQL command.

```sql
CREATE TABLE Employees (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(100),
    Position VARCHAR(100),
    Salary DECIMAL(10, 2)
);
```

This command creates a table named `Employees` with three columns: `ID`, `Name`, `Position`, and `Salary`. The `ID` column is auto-incrementing and serves as the primary key.

## Manipulating Data

### Inserting Data

To insert data into a table, use the `INSERT INTO` SQL command.

```sql
INSERT INTO Employees (Name, Position, Salary)
VALUES ('John Doe', 'Developer', 3000.00);
```

This command inserts a new record into the `Employees` table with the name `John Doe`, position `Developer`, and salary `3000.00`.

### Selecting Data

To retrieve data from a table, use the `SELECT` SQL command.

```sql
SELECT * FROM Employees;
```

This command selects all rows from the `Employees` table.

To filter data, use the `WHERE` clause.

```sql
SELECT Name, Position
FROM Employees
WHERE Salary > 2500;
```

This command selects the names and positions of employees whose salary is greater than `2500`.

### Updating Data

To update data in a table, use the `UPDATE` SQL command.

```sql
UPDATE Employees
SET Salary = 3500.00
WHERE Name = 'John Doe';
```

This command updates the salary of the employee `John Doe` to `3500.00`.

### Deleting Data

To delete data from a table, use the `DELETE` SQL command.

```sql
DELETE FROM Employees
WHERE Name = 'John Doe';
```

This command deletes the record from the `Employees` table where the employee's name is `John Doe`.

## Database Management

### Creating Indexes

Indexes speed up data retrieval in tables. To create an index, use the `CREATE INDEX` SQL command.

```sql
CREATE INDEX idx_position
ON Employees (Position);
```

This command creates an index called `idx_position` on the `Position` column in the `Employees` table.

### Creating Views

A view is a saved query that can be used to display data from a table. To create a view, use the `CREATE VIEW` SQL command.

```sql
CREATE VIEW DeveloperSalaries AS
SELECT Name, Salary
FROM Employees
WHERE Position = 'Developer';
```

This command creates a view called `DeveloperSalaries`, which contains the names and salaries of developers.

## Backing Up and Restoring Data

### Backing Up Data

To back up a MySQL database, use the `mysqldump` tool.

```bash
mysqldump -u root -p my_database > my_database_backup.sql
```

This command backs up the `my_database` database to the `my_database_backup.sql` file.

### Restoring Data

To restore a backed-up database, use the `mysql` tool.

```bash
mysql -u root -p my_database < my_database_backup.sql
```

This command restores the `my_database` database from the `my_database_backup.sql` file.

## Sources

- [MySQL Official Documentation](https://dev.mysql.com/doc/)
- [SQL for Dummies by Allen G. Taylor](https://www.amazon.com/SQL-Dummies-Computer-Tech/dp/1119527074)
- [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)
- [MySQL Performance Blog](https://www.percona.com/blog/)

## Review Questions or Exercises

- What is MySQL, and how does it differ from other database systems?
- Write an SQL command to create a new database named "Company."
- Create a table named "Departments" with the following columns: ID (primary key), DepartmentName (text), Location (text).
- Write an SQL query to insert a new record into the "Departments" table: IT department, located in Tallinn.
- Write an SQL command to update the department name with ID 1 to "Human Resources."
- Write an SQL query to delete the record from the "Departments" table where the department name is "IT."

## Exercise

- Create a new database named "School."
- Create a table named "Students" with the following columns: ID (primary key), FirstName (text), LastName (text), Age (number), Email (text).
- Insert three sample records into the "Students" table.
- Write an SQL query to select all students whose age is greater than 18.
- Write an SQL query to update the email of the student with ID 2.
- Write an SQL query to delete the record from the "Students" table where the student's age is less than 16.

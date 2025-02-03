# Relational Databases

Relational databases are widely used data management tools that allow for the storage of data in a structured and organized manner. These databases use a table system to store and manage data and rely on a relational model first described by Edgar F. Codd in 1970. This chapter introduces the key concepts, structure, advantages, and use cases of relational databases.

![Relational Databases](Relational-Database.webp)

Image source: [Dall-E by OpenAI](https://openai.com/)

- [Relational Databases](#relational-databases)
  - [Learning Outcomes](#learning-outcomes)
  - [Key Concepts of Relational Databases](#key-concepts-of-relational-databases)
    - [Tables](#tables)
    - [Primary Key](#primary-key)
    - [Foreign Key](#foreign-key)
    - [Indexes](#indexes)
  - [Terminology of Relational Databases](#terminology-of-relational-databases)
  - [SQL and Relational Databases](#sql-and-relational-databases)
    - [Creating a Database and Tables](#creating-a-database-and-tables)
    - [Adding Data](#adding-data)
    - [Reading Data](#reading-data)
    - [Updating Data](#updating-data)
    - [Deleting Data](#deleting-data)
    - [Creating Relationships Between Tables](#creating-relationships-between-tables)
  - [Advantages and Limitations of Relational Databases](#advantages-and-limitations-of-relational-databases)
    - [Advantages](#advantages)
    - [Limitations](#limitations)
  - [Sources](#sources)
  - [Review Questions or Exercises](#review-questions-or-exercises)
  - [Exercise](#exercise)

## Learning Outcomes

By the end of this chapter, learners should be able to:

- Explain what a relational database is and how it works;
- Describe the key components and terminology of relational databases;
- Create and manage data in a relational database using SQL;
- Understand the advantages and limitations of relational databases.

## Key Concepts of Relational Databases

### Tables

Tables are the fundamental elements of relational databases, consisting of rows and columns. Each table represents a specific dataset (e.g., customers, orders, products).

- **Row:** A data entry in the table. Each row contains data according to the table's columns. A row can also be referred to as a record or tuple.
- **Column:** A property or attribute of the table, also known as a field.

Example of a table:

| ID  | Name  | Age |
| --- | ----- | --- |
| 1   | Jaan  | 25  |
| 2   | Mari  | 30  |
| 3   | Kalle | 22  |

### Primary Key

A primary key is a unique identifier that distinguishes each row in a table. The primary key ensures that each record is unique.

### Foreign Key

A foreign key is a reference to a primary key in another table. It allows the creation of relationships between tables.

### Indexes

Indexes speed up data searches and query execution by providing references to the rows of a table.

## Terminology of Relational Databases

- **Relation:** A table that contains related data.
- **Attribute:** A column in a table that defines a data type.
- **Tuple:** A row in a table that contains a data unit.
- **Domain:** The set of all possible values that an attribute can have.
- **Referential Integrity:** Ensures that all foreign keys point to existing records in related tables.

## SQL and Relational Databases

**SQL (Structured Query Language)** is the standard language used to communicate with and manage relational databases. SQL enables the creation, reading, updating, and deleting of data (CRUD operations).

### Creating a Database and Tables

```sql
CREATE DATABASE my_database;

USE my_database;

CREATE TABLE Users (
    ID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(100),
    Age INT
);
```

When creating tables, each column's data type and constraints (e.g., primary key, foreign key) are defined. In the example above, `ID` is a primary key that auto-increments, `Name` is a text field with a maximum length of 100 characters, and `Age` is an integer.

### Adding Data

```sql
INSERT INTO Users (Name, Age) VALUES ('Jaan', 25);
INSERT INTO Users (Name, Age) VALUES ('Mari', 30);
INSERT INTO Users (Name, Age) VALUES ('Kalle', 22);
```

### Reading Data

```sql
SELECT * FROM Users;

SELECT Name, Age FROM Users WHERE Age > 25;
```

Response:

| Name | Age |
| ---- | --- |
| Mari | 30  |

As seen in the previous example, SQL allows selecting specific columns and filtering results based on conditions.

### Updating Data

```sql
UPDATE Users SET Age = 26 WHERE Name = 'Jaan';
```

### Deleting Data

```sql
DELETE FROM Users WHERE Name = 'Kalle';
```

> **Note:** Before deleting data, ensure you are certain you want to remove the data, as deleted data cannot be restored. Use the `WHERE` clause to specify which data to delete.

### Creating Relationships Between Tables

```sql
CREATE TABLE Orders (
    OrderID INT AUTO_INCREMENT PRIMARY KEY,
    UserID INT,
    Product VARCHAR(100),
    FOREIGN KEY (UserID) REFERENCES Users(ID)
);
```

In this example, the `Orders` table is created, which includes the `UserID` field that is a foreign key referencing the `Users` table. This relationship allows creating links between the two tables, meaning that each order in the `Orders` table is associated with a specific user in the `Users` table.

## Advantages and Limitations of Relational Databases

### Advantages

- **Structured Data:** Tables and relationships ensure structured and logical organization of data.
- **Data Integrity:** Primary and foreign keys, along with referential integrity, ensure data accuracy and consistency.
- **Power of SQL:** SQL provides strong and flexible tools for data management and querying.

### Limitations

- **Horizontal Scalability:** Horizontal scaling (partitioning the database across multiple servers) can be complex.
- **Complex Data Models:** Very complex and dynamic data models may require intricate schema design and maintenance.
- **Performance:** Performance may degrade with large datasets, especially with complex queries.

## Sources

- [MySQL Documentation](https://dev.mysql.com/doc/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)

## Review Questions or Exercises

- What is a relational database, and how does it differ from other types of databases?
- Describe what a primary key and a foreign key are, and provide an example.
- How do you create a database and tables using SQL?
- Write an SQL query that selects all users whose age is less than 25.
- How do you establish a relationship between two tables using a foreign key?

## Exercise

- Create a relational database named "Library."
- Create a table "Books" with the columns: `ID` (primary key), `Title`, `Author`, `PublishedYear`.
- Create a table "Borrowers" with the columns: `ID` (primary key), `Name`, `MembershipDate`.
- Create a table "Loans" with the columns: `LoanID` (primary key), `BookID` (foreign key referencing "Books" table), `BorrowerID` (foreign key referencing "Borrowers" table), `LoanDate`, `ReturnDate`.
- Insert sample data into each table.
- Write an SQL query that displays all borrowed books along with the names of the borrowers and loan dates.

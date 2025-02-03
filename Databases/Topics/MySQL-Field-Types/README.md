# MySQL: Overview of Field Types

MySQL provides various data types for storing data, each suited for specific types of data and requirements. Choosing the right data type is crucial to ensure the efficiency, performance, and integrity of the database. This chapter provides an overview of MySQL field types and their usage.

- [MySQL: Overview of Field Types](#mysql-overview-of-field-types)
  - [Learning Outcomes](#learning-outcomes)
  - [MySQL Data Types](#mysql-data-types)
    - [Numeric Data Types](#numeric-data-types)
      - [Integers](#integers)
      - [Floating-Point Numbers](#floating-point-numbers)
    - [Date and Time Data Types](#date-and-time-data-types)
    - [Text Data Types](#text-data-types)
    - [Binary Data Types](#binary-data-types)
    - [Other Data Types](#other-data-types)
  - [Additional Field Attributes](#additional-field-attributes)
  - [Sources](#sources)
  - [Review Questions or Exercises](#review-questions-or-exercises)
  - [Exercise](#exercise)

## Learning Outcomes

By the end of this chapter, learners should be able to:

- Explain the various MySQL data types and their properties;
- Choose appropriate data types based on the nature of the data;
- Use different data types while creating and modifying MySQL tables.

## MySQL Data Types

MySQL field types can be categorized into the following groups:

- Numeric data types
- Date and time data types
- Text data types
- Binary data types
- Other data types

### Numeric Data Types

Numeric data types are used to store numerical data. These can be further divided into integers and floating-point numbers.

#### Integers

- **TINYINT:** Very small integer (range: -128 to 127).
- **SMALLINT:** Small integer (range: -32,768 to 32,767).
- **MEDIUMINT:** Medium-sized integer (range: -8,388,608 to 8,388,607).
- **INT or INTEGER:** Regular integer (range: -2,147,483,648 to 2,147,483,647).
- **BIGINT:** Large integer (range: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807).

Example:

```sql
CREATE TABLE Numbers (
    small_num SMALLINT,
    medium_num MEDIUMINT,
    large_num BIGINT
);
```

#### Floating-Point Numbers

- **FLOAT:** Floating-point number with lower precision.
- **DOUBLE:** Floating-point number with higher precision.
- **DECIMAL or NUMERIC:**  Fixed-point number with a defined precision and scale.

Näide:

```sql
CREATE TABLE Prices (
    price_float FLOAT,
    price_double DOUBLE,
    price_decimal DECIMAL(10, 2)
);
```

### Date and Time Data Types

Date and time data types are used to store temporal data.

- **DATE:** Date (format: YYYY-MM-DD).
- **TIME:** Time (format: HH:MI:SS).
- **DATETIME:** Date and time (combined format: YYYY-MM-DD HH:MI:SS).
- **TIMESTAMP:** Timestamp (stored in UTC).
- **YEAR:** Year (format: YYYY).

Example:

```sql
CREATE TABLE Events (
    event_date DATE,
    event_time TIME,
    event_timestamp TIMESTAMP
);
```

### Text Data Types

Text data types are used to store strings of letters and numbers.

- **CHAR:** Fixed-length string (up to 255 characters).
- **VARCHAR:** Variable-length string (up to 65,535 characters).
- **TINYTEXT:** Very small text (up to 255 characters).
- **TEXT:** Small text (up to 65,535 characters).
- **MEDIUMTEXT:** Medium-sized text (up to 16,777,215 characters).
- **LONGTEXT:** Large text (up to 4,294,967,295 characters).

Example:

```sql
CREATE TABLE Messages (
    message_short CHAR(50),
    message_long TEXT
);
```

### Binary Data Types

Binary data types are used to store binary data, such as images or files.

- **BINARY:** Fixed-length binary string.
- **VARBINARY:** Variable-length binary string.
- **TINYBLOB:** Small binary object (up to 255 bytes).
- **BLOB:** Binary object (up to 65,535 bytes)
- **MEDIUMBLOB:** Medium-sized binary object (up to 16,777,215 bytes).
- **LONGBLOB:** Large binary object (up to 4,294,967,295 bytes).

Example:

```sql
CREATE TABLE Files (
    file_name VARCHAR(255),
    file_data BLOB
);
```

### Other Data Types

- **ENUM:** Enumerated type, allowing one value from a defined list.
- **SET:** Set type, allowing zero or more values from a defined list.

Example:

```sql
CREATE TABLE Products (
    product_name VARCHAR(100),
    product_status ENUM('available', 'out_of_stock', 'discontinued')
);
```

## Additional Field Attributes

Fields can include various attributes that define constraints and behavior. Common field attributes include:

- `NOT NULL`: Ensures the value cannot be NULL.
- `UNIQUE`: Ensures the value is unique.
- `DEFAULT value`: Specifies a default value if none is provided.
- `AUTO_INCREMENT`: Automatically increments the column value for each new row.
- `PRIMARY KEY`: A unique identifier for each record.
- `FOREIGN KEY`: Defines relationships between tables.
- ...

## Sources

- [MySQL Official Documentation](https://dev.mysql.com/doc/)
- [W3Schools MySQL Data Types](https://www.w3schools.com/sql/sql_datatypes.asp)
- [MySQL Performance Blog](https://www.percona.com/blog/)

## Review Questions or Exercises

- What are MySQL data types, and why are they important?
- Write an SQL command to create a table named "Employees" with the following columns: ID (primary key, integer), Name (variable character string, max 100 characters), Position (fixed character string, 50 characters), Salary (decimal number with 10 digits and 2 decimal places).
- Which MySQL data type is most suitable for storing large text documents? Write an example.
-Write an SQL command to create a table "Orders" with the following columns: OrderID (primary key, integer), OrderDate (date), TotalAmount (decimal number with 10 digits and 2 decimal places).

## Exercise

- Create a new database named "Library".
- Create a table named "Books" with the following columns: ID (primary key, integer), Title (variable character string, max 255 characters), Author (variable character string, max 100 characters), PublishedYear (year), Genre (enum with values 'Fiction', 'Non-Fiction', 'Sci-Fi', 'Biography'), CoverImage (blob).
- Insert three sample records into the "Books" table.
- Write an SQL query to select all books published after the year 2000.
- Write an SQL query to update the genre of the book titled "1984" to "Sci-Fi".
Write an SQL query to delete the record from the "Books" table where the author's name is "George Orwell".

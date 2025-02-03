# Making MySQL Queries (CRUD)

CRUD (Create, Read, Update, Delete) operations are the fundamental database operations used for managing data. In this learning material, we will cover how to perform CRUD operations in MySQL using the previously created blog database, which includes tables for users, posts, and comments.

![MySQL queries](MySQL-Queries.webp)

Image source: Dall-E by OpenAI

- [Making MySQL Queries (CRUD)](#making-mysql-queries-crud)
  - [Learning Outcomes](#learning-outcomes)
  - [Creating the Database and Tables](#creating-the-database-and-tables)
  - [CRUD Operations](#crud-operations)
    - [1. Adding Data (Create)](#1-adding-data-create)
      - [Adding Users](#adding-users)
      - [Adding Posts](#adding-posts)
      - [Adding Comments](#adding-comments)
    - [2. Reading Data (Read)](#2-reading-data-read)
      - [Reading All Users](#reading-all-users)
      - [Reading Specific User Data](#reading-specific-user-data)
      - [Reading Posts and Their Authors](#reading-posts-and-their-authors)
      - [Reading Comments with Posts and Authors Data](#reading-comments-with-posts-and-authors-data)
    - [3. Updating Data (Update)](#3-updating-data-update)
      - [Updating User Data](#updating-user-data)
      - [Updating Post Content](#updating-post-content)
    - [4. Deleting Data (Delete)](#4-deleting-data-delete)
      - [Deleting a User](#deleting-a-user)
      - [Deleting a Post](#deleting-a-post)
      - [Deleting a Comment](#deleting-a-comment)
  - [Complete Example](#complete-example)
    - [Adding (Create)](#adding-create)
    - [Reading (Read)](#reading-read)
    - [Updating (Update)](#updating-update)
    - [Deleting (Delete)](#deleting-delete)
  - [Using Additional Parameters in MySQL Queries](#using-additional-parameters-in-mysql-queries)
  - [LIMIT](#limit)
    - [Example: Retrieving the First 10 Rows from the Users Table](#example-retrieving-the-first-10-rows-from-the-users-table)
  - [ORDER BY](#order-by)
    - [Example: Sorting Users by Username in Ascending Order](#example-sorting-users-by-username-in-ascending-order)
    - [Example: Sorting Users by Creation Date in Descending Order](#example-sorting-users-by-creation-date-in-descending-order)
  - [GROUP BY](#group-by)
    - [Example: Counting the Number of Posts by User](#example-counting-the-number-of-posts-by-user)
  - [AND, OR](#and-or)
    - [Example: Users with a Certain Email Domain and Registered After a Certain Date](#example-users-with-a-certain-email-domain-and-registered-after-a-certain-date)
    - [Example: Users with a Certain Email Domain or Registered After a Certain Date](#example-users-with-a-certain-email-domain-or-registered-after-a-certain-date)
  - [DISTINCT](#distinct)
    - [Example: Retrieving All Unique Email Domains from the Users Table](#example-retrieving-all-unique-email-domains-from-the-users-table)
  - [Examples of Using Additional Parameters](#examples-of-using-additional-parameters)
    - [Example: Retrieving a List of Users with Restrictions and Sorting](#example-retrieving-a-list-of-users-with-restrictions-and-sorting)
    - [Example: Counting Users by Domain and Sorting the Results](#example-counting-users-by-domain-and-sorting-the-results)
    - [Complete Example: Using Additional Parameters in a Blog Database](#complete-example-using-additional-parameters-in-a-blog-database)
      - [Counting and Sorting Posts by User](#counting-and-sorting-posts-by-user)

## Learning Outcomes

By the end of this material, learners should be able to:

- Create new records (Create) in database tables.
- Read and query data (Read) from tables.
- Update existing records (Update) in tables.
- Delete records (Delete) from tables.

## Creating the Database and Tables

We will start by creating a database that contains three tables: `users`, `posts`, and `comments`.

First, create the database using the following SQL command:

```sql
CREATE DATABASE blog;
```

Next, create the tables using the following SQL commands:

```sql
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(50) NOT NULL,
  email VARCHAR(100) NOT NULL,
  password VARCHAR(100) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE posts (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user_id INT,
  title VARCHAR(100) NOT NULL,
  content TEXT NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE comments (
  id INT AUTO_INCREMENT PRIMARY KEY,
  post_id INT,
  user_id INT,
  content TEXT NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (post_id) REFERENCES posts(id),
  FOREIGN KEY (user_id) REFERENCES users(id)
);
```

These SQL commands create three tables: `users`, `posts`, and `comments`. Each table contains different columns that define the structure of the data and the relationships with other tables. The comments table includes foreign keys referencing the posts and users tables, meaning that we cannot add comments without a corresponding post or user.

## CRUD Operations

### 1. Adding Data (Create)

To add data to a table, use the `INSERT INTO` command.

#### Adding Users

```sql
INSERT INTO users (username, email, password) VALUES ('alice', 'alice@example.com', 'securepassword');
INSERT INTO users (username, email, password) VALUES ('bob', 'bob@example.com', 'securepassword');
```

#### Adding Posts

```sql
INSERT INTO posts (user_id, title, content) VALUES (1, 'Alice First Post', 'This is the content of Alice\'s first post.');
INSERT INTO posts (user_id, title, content) VALUES (2, 'Bob First Post', 'This is the content of Bob\'s first post.');
```

#### Adding Comments

```sql
INSERT INTO comments (post_id, user_id, content) VALUES (1, 2, 'This is Bob\'s comment on Alice\'s first post.');
INSERT INTO comments (post_id, user_id, content) VALUES (2, 1, 'This is Alice\'s comment on Bob\'s first post.');
```

### 2. Reading Data (Read)

To read and query data from tables, use the `SELECT` command.

#### Reading All Users

```sql
SELECT * FROM users;
```

#### Reading Specific User Data

```sql
SELECT * FROM users WHERE username = 'alice';
```

> The `WHERE` condition restricts the query results based on specified criteria.

#### Reading Posts and Their Authors

```sql
SELECT posts.title, posts.content, users.username
FROM posts
JOIN users ON posts.user_id = users.id;
```

> The `JOIN` clause combines two tables based on specified conditions, allowing us to combine data from multiple tables in one query.

#### Reading Comments with Posts and Authors Data

```sql
SELECT comments.content AS comment, posts.title AS post_title, users.username AS author
FROM comments
JOIN posts ON comments.post_id = posts.id
JOIN users ON comments.user_id = users.id;
```

### 3. Updating Data (Update)

To update existing records in tables, use the `UPDATE` command.

#### Updating User Data

```sql
UPDATE users
SET email = 'newalice@example.com'
WHERE username = 'alice';
```

#### Updating Post Content

```sql
UPDATE posts
SET content = 'This is the updated content of Alice\'s first post.'
WHERE id = 1;
```

### 4. Deleting Data (Delete)

To delete records from tables, use the `DELETE` command.

#### Deleting a User

```sql
DELETE FROM users
WHERE username = 'bob';
```

> Always ensure that you delete the correct record by using the `WHERE` condition.

#### Deleting a Post

```sql
DELETE FROM posts
WHERE id = 2;
```

#### Deleting a Comment

```sql
DELETE FROM comments
WHERE id = 1;
```

## Complete Example

### Adding (Create)

```sql
-- Adding Users
INSERT INTO users (username, email, password) VALUES ('alice', 'alice@example.com', 'securepassword');
INSERT INTO users (username, email, password) VALUES ('bob', 'bob@example.com', 'securepassword');

-- Adding Posts
INSERT INTO posts (user_id, title, content) VALUES (1, 'Alice First Post', 'This is the content of Alice\'s first post.');
INSERT INTO posts (user_id, title, content) VALUES (2, 'Bob First Post', 'This is the content of Bob\'s first post.');

-- Adding Comments
INSERT INTO comments (post_id, user_id, content) VALUES (1, 2, 'This is Bob\'s comment on Alice\'s first post.');
INSERT INTO comments (post_id, user_id, content) VALUES (2, 1, 'This is Alice\'s comment on Bob\'s first post.');
```

### Reading (Read)

```sql
-- Reading All Users
SELECT * FROM users;

-- Reading Specific User Data
SELECT * FROM users WHERE username = '

alice';

-- Reading Posts and Their Authors
SELECT posts.title, posts.content, users.username
FROM posts
JOIN users ON posts.user_id = users.id;

-- Reading Comments with Posts and Authors Data
SELECT comments.content AS comment, posts.title AS post_title, users.username AS author
FROM comments
JOIN posts ON comments.post_id = posts.id
JOIN users ON comments.user_id = users.id;
```

### Updating (Update)

```sql
-- Updating User Data
UPDATE users
SET email = 'newalice@example.com'
WHERE username = 'alice';

-- Updating Post Content
UPDATE posts
SET content = 'This is the updated content of Alice\'s first post.'
WHERE id = 1;
```

### Deleting (Delete)

```sql
-- Deleting a User
DELETE FROM users
WHERE username = 'bob';

-- Deleting a Post
DELETE FROM posts
WHERE id = 2;

-- Deleting a Comment
DELETE FROM comments
WHERE id = 1;
```

## Using Additional Parameters in MySQL Queries

MySQL offers several powerful SQL commands and clauses to help retrieve data accurately and efficiently. In this section, we will cover useful SQL commands and clauses, including LIMIT, ORDER BY, GROUP BY, AND, OR, DISTINCT, and more.

## LIMIT

The LIMIT clause is used to restrict the number of results returned by a query. It is useful for managing large datasets, especially when working with pagination.

### Example: Retrieving the First 10 Rows from the Users Table

```sql
SELECT * FROM users LIMIT 10;
```

## ORDER BY

The ORDER BY clause is used to sort the results of a query by a specified column. You can sort the results in either ascending (ASC) or descending (DESC) order.

### Example: Sorting Users by Username in Ascending Order

```sql
SELECT * FROM users ORDER BY username ASC;
```

### Example: Sorting Users by Creation Date in Descending Order

```sql
SELECT * FROM users ORDER BY created_at DESC;
```

## GROUP BY

The GROUP BY clause is used to group rows that share certain properties, and it is typically used with aggregate functions like COUNT, SUM, AVG, MAX, and MIN.

### Example: Counting the Number of Posts by User

```sql
SELECT user_id, COUNT(*) AS post_count
FROM posts
GROUP BY user_id;
```

## AND, OR

AND and OR operators allow you to specify multiple conditions in the WHERE clause. The AND operator returns rows that satisfy all conditions, while the OR operator returns rows that satisfy at least one condition.

### Example: Users with a Certain Email Domain and Registered After a Certain Date

```sql
SELECT * FROM users
WHERE email LIKE '%@example.com' AND created_at > '2021-01-01';
```

### Example: Users with a Certain Email Domain or Registered After a Certain Date

```sql
SELECT * FROM users
WHERE email LIKE '%@example.com' OR created_at > '2021-01-01';
```

## DISTINCT

The DISTINCT clause is used to remove duplicate values from the results of a query. It returns only unique rows.

### Example: Retrieving All Unique Email Domains from the Users Table

```sql
SELECT DISTINCT SUBSTRING_INDEX(email, '@', -1) AS domain
FROM users;
```

## Examples of Using Additional Parameters

### Example: Retrieving a List of Users with Restrictions and Sorting

```sql
SELECT * FROM users
WHERE email LIKE '%@example.com' AND created_at > '2021-01-01'
ORDER BY created_at DESC
LIMIT 5;
```

### Example: Counting Users by Domain and Sorting the Results

```sql
SELECT SUBSTRING_INDEX(email, '@', -1) AS domain, COUNT(*) AS user_count
FROM users
GROUP BY domain
ORDER BY user_count DESC;
```

### Complete Example: Using Additional Parameters in a Blog Database

#### Counting and Sorting Posts by User

```sql
SELECT users.username, COUNT(posts.id) AS post_count
FROM users
LEFT JOIN posts ON users.id = posts.user_id
GROUP BY users.username
ORDER BY post_count DESC
LIMIT 10;
```

This query joins the users and posts tables, counts the number of posts for each user, groups the results by username, and sorts them by the number of posts in descending order, limiting the output to the first 10 results.

# MySQL JOINs

MySQL JOINs are a powerful way to query and combine data from different tables. JOINs allow rows from two or more tables to be connected based on primary and foreign keys. In this learning material, we will explore the various types of JOINs, how to use them, and provide examples of practical queries.

![SQL JOIN](SQL-JOIN.webp)

Image source: [Dall-E by OpenAI](https://openai.com/)

- [MySQL JOINs](#mysql-joins)
  - [Learning Outcomes](#learning-outcomes)
  - [JOIN Basics](#join-basics)
    - [Types of JOINs](#types-of-joins)
  - [INNER JOIN](#inner-join)
    - [Example: Using INNER JOIN](#example-using-inner-join)
      - [Users and Posts](#users-and-posts)
    - [Practical Example: Users and Comments](#practical-example-users-and-comments)
  - [LEFT JOIN](#left-join)
    - [Example: Using LEFT JOIN](#example-using-left-join)
      - [All Users and Their Posts](#all-users-and-their-posts)
    - [Practical Example: All Users and Their Comments](#practical-example-all-users-and-their-comments)
  - [RIGHT JOIN](#right-join)
    - [Example: Using RIGHT JOIN](#example-using-right-join)
      - [All Posts and Their Authors](#all-posts-and-their-authors)
    - [Practical Example: All Comments and Their Authors](#practical-example-all-comments-and-their-authors)
  - [FULL JOIN](#full-join)
    - [Example: Using FULL JOIN](#example-using-full-join)
      - [All Users and Posts](#all-users-and-posts)
    - [Practical Example: All Users and Comments](#practical-example-all-users-and-comments)
  - [Complete Example: JOINs in a Blog Database](#complete-example-joins-in-a-blog-database)
    - [Creating the Database and Tables](#creating-the-database-and-tables)
    - [Inserting Data](#inserting-data)
    - [Using JOINs](#using-joins)
      - [INNER JOIN: Users and Posts](#inner-join-users-and-posts)
      - [LEFT JOIN: All Users and Their Posts](#left-join-all-users-and-their-posts)
      - [RIGHT JOIN: All Posts and Their Authors](#right-join-all-posts-and-their-authors)
      - [FULL JOIN: All Users and Posts](#full-join-all-users-and-posts)

## Learning Outcomes

By the end of this learning material, learners should be able to:

- Explain the principles of JOINs and how to use them in MySQL;
- Use different types of JOINs (INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN);
- Write complex queries that combine data from multiple tables;
- Apply JOINs in practical examples with a blog database.

## JOIN Basics

### Types of JOINs

1. **INNER JOIN**: Returns only rows that have matching values in both tables.
2. **LEFT JOIN**: Returns all rows from the left table, and the matched rows from the right table. If there is no match, the result is NULL on the right side.
3. **RIGHT JOIN**: Returns all rows from the right table, and the matched rows from the left table. If there is no match, the result is NULL on the left side.
4. **FULL JOIN**: Returns all rows when there is a match in either the left or right table. MySQL does not support `FULL JOIN` directly, but it can be achieved using `UNION`.

> "Left" and "right" refer to the order of the tables in the query. The left table is the first table, and the right table is the second table.

## INNER JOIN

INNER JOIN returns only rows that have a match in both tables.

### Example: Using INNER JOIN

#### Users and Posts

```sql
SELECT users.username, posts.title FROM users
  INNER JOIN posts ON users.id = posts.user_id;
```

This query returns the usernames of all users and the titles of their posts, showing only where there is a match between users and posts.

### Practical Example: Users and Comments

```sql
SELECT users.username, comments.content
  FROM users
  INNER JOIN comments ON users.id = comments.user_id;
```

This query returns the usernames of all users and the content of their comments.

## LEFT JOIN

LEFT JOIN returns all rows from the left table and the matched rows from the right table. If there is no match, NULL is returned for the right table's columns.

### Example: Using LEFT JOIN

#### All Users and Their Posts

```sql
SELECT users.username, posts.title
  FROM users
  LEFT JOIN posts ON users.id = posts.user_id;
```

This query returns the usernames of all users and the titles of their posts. If a user has no posts, the post title will be NULL.

### Practical Example: All Users and Their Comments

```sql
SELECT users.username, comments.content
  FROM users
  LEFT JOIN comments ON users.id = comments.user_id;
```

This query returns the usernames of all users and the content of their comments. If a user has no comments, the comment content will be NULL.

## RIGHT JOIN

RIGHT JOIN returns all rows from the right table and the matched rows from the left table. If there is no match, NULL is returned for the left table's columns.

### Example: Using RIGHT JOIN

#### All Posts and Their Authors

```sql
SELECT users.username, posts.title
  FROM users
  RIGHT JOIN posts ON users.id = posts.user_id;
```

This query returns the titles of all posts and their authors' usernames. If a post has no associated author (which is rare), the author's username will be NULL.

### Practical Example: All Comments and Their Authors

```sql
SELECT users.username, comments.content
FROM users
RIGHT JOIN comments ON users.id = comments.user_id;
```

This query returns the content of all comments and their authors' usernames. If a comment has no associated author, the author's username will be NULL.

## FULL JOIN

FULL JOIN returns all rows where there is a match in either the left or right table. Since MySQL doesn't directly support `FULL JOIN`, it can be done using a `UNION`.

### Example: Using FULL JOIN

#### All Users and Posts

```sql
SELECT users.username, posts.title
FROM users
LEFT JOIN posts ON users.id = posts.user_id
UNION
SELECT users.username, posts.title
FROM posts
LEFT JOIN users ON posts.user_id = users.id;
```

This query returns all users and their posts, as well as posts that have no matching users and users with no posts.

### Practical Example: All Users and Comments

```sql
SELECT users.username, comments.content
FROM users
LEFT JOIN comments ON users.id = comments.user_id
UNION
SELECT users.username, comments.content
FROM comments
LEFT JOIN users ON comments.user_id = users.id;
```

This query returns all users and their comments, as well as comments that have no matching users and users with no comments.

## Complete Example: JOINs in a Blog Database

### Creating the Database and Tables

```sql
CREATE DATABASE blog;
USE blog;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE posts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE comments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    post_id INT NOT NULL,
    user_id INT NOT NULL,
    content TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (post_id) REFERENCES posts(id),
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

### Inserting Data

```sql
-- Inserting Users
INSERT INTO users (username, email, password) VALUES ('alice', 'alice@example.com', 'securepassword');
INSERT INTO users (username, email, password) VALUES ('bob', 'bob@example.com', 'securepassword');

-- Inserting Posts
INSERT INTO posts (user_id, title, content) VALUES (1, 'Alice First Post', 'This is the content of Alice\'s first post.');
INSERT INTO posts (user_id, title, content) VALUES (2, 'Bob First Post', 'This is the content of Bob\'s first post.');

-- Inserting Comments
INSERT INTO comments (post_id, user_id, content) VALUES (1, 2, 'This is Bob\'s comment on Alice\'s first post.');
INSERT INTO comments (post_id, user_id, content) VALUES (2, 1, 'This is Alice\'s comment on Bob\'s first post.');
```

### Using JOINs

#### INNER JOIN: Users and Posts

```sql
SELECT users.username, posts.title
FROM users
INNER JOIN posts ON users.id = posts.user_id;
```

#### LEFT JOIN: All Users and Their Posts

```sql
SELECT users.username, posts.title
FROM users
LEFT JOIN posts ON users.id = posts.user_id;
```

#### RIGHT JOIN: All Posts and Their Authors

```sql
SELECT users.username, posts.title
FROM users
RIGHT JOIN posts ON users.id = posts.user_id;
```

#### FULL JOIN: All Users and Posts

```sql
SELECT users.username, posts.title
FROM users
LEFT JOIN posts ON users.id = posts.user_id
UNION
SELECT users.username, posts.title
FROM posts
LEFT JOIN users ON posts.user_id = users.id;
```

---
marp: true
---

# Web Development

## Back-End Development


---

## Today's Topics

- Review of the previous lecture
- [JOIN Statements in MySQL](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Databases/Topics/MySQL-Join/README.md)
- [Error Handling in Express API](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Back-End-Frameworks/Topics/Error-Handling/README.md)
- [Logging in an Express Application](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Back-End-Frameworks/Topics/Logging/README.md)

---

## What Did We Discuss Last Time?

---

## JOIN Statements in MySQL

MySQL JOINs allow data to be queried and combined from different tables. JOINs enable us to combine rows from two or more tables that are related through primary and foreign keys.

---

## Types of JOINs

- `INNER JOIN`
- `LEFT JOIN`
- `RIGHT JOIN`
- `FULL JOIN`

---

## `INNER JOIN`

`INNER JOIN` returns only the rows with matches in both tables.

```sql
SELECT column_name(s)
  FROM left_table
  INNER JOIN right_table
  ON left_table.column_name = right_table.column_name;
```

> Left and right tables refer to the table order in the query.
---

## Using `INNER JOIN`

Tasks with user data:

```sql
SELECT users.firstName, users.lastName, todos.title, todos.description, todos.is_done
  FROM todos
  INNER JOIN users
  ON todos.user_id = users.id
WHERE todos.deleted_at IS NULL;
```

---

## `LEFT JOIN`

`LEFT JOIN` returns all rows from the left table and the matching rows from the right table. If there is no match, the right table columns contain NULL.

```sql
SELECT column_name(s)
  FROM left_table
  INNER JOIN right_table
  ON left_table.column_name = right_table.column_name;
```

---

## Using `LEFT JOIN`

Tasks with user data:

```sql
SELECT users.firstName, users.lastName, todos.title, todos.description, todos.is_done
  FROM todos
  LEFT JOIN users
  ON todos.user_id = users.id
WHERE todos.deleted_at IS NULL;
```

> As shown,`LEFT JOIN` is similar to  `INNER JOIN`, but the difference appears when there are rows without matches.

---

## `RIGHT JOIN`

`RIGHT JOIN` returns all rows from the right table and the matching rows from the left table. If there is no match, the left table columns contain NULL.

---

## `FULL JOIN`

FULL JOIN returns all rows when there is a match in either left or right table. MySQL does not directly support `FULL JOIN`, but it can be achieved with `UNION`.

---

## Error Handling in Express API

Error handling is an important part of any software development. It helps identify, track, and resolve issues within software. Currently, in our API, we handle errors within controllers by forming an appropriate client response with an error message and returning it.

The challenge with this approach is that if we have many controllers, we must write the same error-handling code in each one. Additionally, if we want to start logging errors at some point, we would have to add logging code for each controller.
---

## Error Handling Middleware

In an Express API, we can separate error handling from controllers and centralize it in one place by using Express middleware.

---

## Using Middleware

Error-handling middleware includes four parameters: `err`, `req`, `res` and `next`. Unlike regular middleware,  `err`  is a parameter containing the error object. In Express, an error object includes the error code, error message, and additional error details. By invoking the `next()`  function with the error object, we pass the error directly to the error-handling middleware.

```javascript
const errorHandler = (err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
};

app.use(errorHandler);
```

> The error object includes a `stack` property, which shows the sequence of functions that caused the error, helpful for debugging.

---

## Registering Error Handling Middleware

The error-handling middleware should be registered as the last middleware. Additionally, we need to modify our controllers to function as middleware to send errors to the error-handling middleware via the `next()` function.

```javascript
app.use('/todos', todosRouter);

app.use(errorHandler);
```

---

## Modifying Controllers to Middleware - Original Controller

```javascript
const getAllComments = async (req, res) => {
  const comments = await commentsService.getAllComments();
  if(!comments) {
    return res.status(500).json({
      success: false,
      message: 'Something happened while fetching comments',
    });
  }
  return res.status(200).json({
    success: true,
    message: 'All comments',
    comments,
  });
};
```

---

## Modifying Controllers to Middleware - Updated Controller

```javascript
const getAllComments = async (req, res, next) => {
  try {
    const comments = await commentsService.getAllComments();
    if(!comments) {
      const error = new Error('Something happened while fetching comments');
      error.status = 500;
      throw error;
    }
    return res.status(200).json({
      success: true,
      message: 'All comments',
      comments,
    });
  } catch (error) {
    return next(error);
  }
};
```

---

## What Happens When an Error Occurs?

If an error occurs in the controller (or is returned by a service), we create a new error object with a custom error message. We then add a status code to the error object and "throw" it to be caught by the `catch`block, which passes it to the error-handling middleware via `next()`  The middleware receives the error and sends it to the client. In this way, all errors are handled in one central location, allowing us to log and process them.
---

## Updating Services

Since our services currently return `null`or `false`in case of errors, it can be difficult to determine whether an actual error has occurred. Therefore, we should modify our services to throw an error object with an error code and message.


---

## Modifying a Service

```javascript
const getAllComments = async () => {
  try {
    const comments = await Comment.findAll();
    return comments;
  } catch (error) {
    const err = new Error('Something happened while fetching comments');
    err.status = 500;
    throw err;
  }
};
```

---

## Logging

Logging is the process of recording application activities and events for later analysis. Logging is important for understanding what is happening in the application and for identifying issues.

Logging can also help identify malicious activity and attacks that may threaten the application.

---

## Logging in an Express Application

So far, we have used logging minimally in our application. When an error occurs, we log it to the console and send an error message to the client. However, this is insufficient, as it does not allow us to analyze issues later. It is also challenging to search for specific errors in the console if we have a lot of logs.
---

## Winston logger

Winston is a logging library that allows us to log various events and activities in our application. Winston is highly flexible and allows logging to multiple destinations, such as a file, database, or console.

---

## Installing Winston

To install Winston, use npm:

```bash
npm install winston
```

---

## Using Winston

To use Winston, we need to create a logger object with logging settings like log level, format, and transports specifying where to log.

```javascript
// logger.js
const { createLogger, format, transports } = require('winston');
const { combine, timestamp, printf, errors } = format;

// Custom log format
const logFormat = printf(({ level, message, timestamp, stack }) => {
  return `${timestamp} ${level}: ${stack || message}`;
});

const logger = createLogger({
  level: 'info',
  format: combine(
    timestamp(),
    errors({ stack: true }),
    logFormat
  ),
  transports: [
    new transports.Console(),
    new transports.File({ filename: 'logs/combined.log' }),
    new transports.File({ filename: 'logs/errors.log', level: 'error' }),
  ],
});

module.exports = logger;
```

---

## Using Winston for Error Logging

We want to log all errors to a file for later analysis. To do this, we add logging to our error-handling middleware.

```javascript
const logger = require('./logger');

const errorHandling = (err, req, res, next) => {
  logger.error(err.message, { stack: err.stack });
  res.status(err.status || 500).json({
    success: false,
    message: err.message || 'Internal Server Error',
  });
}
```

We want to log all errors to a file for later analysis. To do this, we add logging to our error-handling middleware. `errors.log` file.

---

## Morgan

Morgan is a logging library designed specifically for logging HTTP requests. Morgan is flexible and allows logging various data, such as request method, URL, status code, and more.

---

## Installing Morgan

To install Morgan, use npm:

```bash
npm install morgan
```

---

## Using Morgan

To use Morgan in an Express application, add it with a specified log format. Here, we use the `combined` log format and configure it to log via Winston.

```javascript
const morgan = require('morgan');
const logger = require('./logger');

app.use(morgan('combined', { stream: { write: message => logger.info(message.trim()) }}));
```

---

## Homework

- Implement error handling in your API
- Log all requests and errors to a file

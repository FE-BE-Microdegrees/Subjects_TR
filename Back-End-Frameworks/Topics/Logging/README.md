---
marp: true

---
# Logging in an Express Application

API usage logging is essential to understand how and when users interact with your API. Logging helps identify patterns, monitor performance, and diagnose issues. In Express, you can implement logging in various ways, using either built-in features or third-party libraries. One of the most popular and powerful logging libraries is `winston`. Additionally, `morgan`, a simple HTTP request logger, can also be used.

![Logging](Logging.webp)

Image Source: Dall-E by OpenAI

- [Logging in an Express Application](#logging-in-an-express-application)
  - [Learning Outcomes](#learning-outcomes)
  - [Installation](#installation)
  - [1. Morgan: HTTP Request Logging](#1-morgan-http-request-logging)
    - [Using Morgan](#using-morgan)
    - [Morgan Logging Formats](#morgan-logging-formats)
    - [Saving Logs to a File](#saving-logs-to-a-file)
  - [2. Winston: Advanced Logging](#2-winston-advanced-logging)
    - [Setting Up Winston](#setting-up-winston)
    - [Integrating Winston with Express](#integrating-winston-with-express)
    - [Explanation](#explanation)
  - [Log Levels](#log-levels)

## Learning Outcomes

By the end of this material, learners should be able to:

- explain the importance of API usage logging;
- install and configure `morgan` and `winston` logging libraries;
- implement API usage logging in Express using `morgan` and `winston`;
- log request details and errors for later analysis.

## Installation

First, install the required libraries:

```bash
npm install morgan winston
```

## 1. **Morgan: HTTP Request Logging**

`morgan` is an HTTP request logging library that can be easily integrated into an Express application.

### Using Morgan

Add `morgan` to your Express application to log all incoming HTTP requests.

```javascript
// app.js
const express = require('express');
const morgan = require('morgan');
const bodyParser = require('body-parser');
const usersRouter = require('./routes/users');

const app = express();

// Morgan logs all requests
app.use(morgan('combined')); // You can choose different log formats (dev, combined, tiny, etc.)

app.use(bodyParser.json());
app.use('/users', usersRouter);

// If no route matches
app.use((req, res, next) => {
  res.status(404).json({
    success: false,
    message: 'Resource not found',
  });
});

// Central error handler
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(err.status || 500).json({
    success: false,
    message: err.message || 'Internal Server Error',
  });
});

module.exports = app;

```

### Morgan Logging Formats

`morgan` offers several logging formats:

- **combined**: Detailed logs with lots of information (good for production).
- **common**: General log format.
- **dev**: Short and colorful log format (good for development).
- **short**: Short log format.
- **tiny**: Very short log format.

### Saving Logs to a File

If you want to save logs to a file for later analysis, you can use `morgan`  with the `fs` module.

```javascript
const fs = require('fs');
const path = require('path');

// Log file stream
const accessLogStream = fs.createWriteStream(path.join(__dirname, 'access.log'), { flags: 'a' });

// Use 'combined' format and save logs to a file
app.use(morgan('combined', { stream: accessLogStream }));

```

## 2. Winston: Advanced Logging

`winston` is a flexible and powerful logging library that can be used for different log levels and formats.

### Setting Up Winston

Create a `winston` logger and integrate it into the Express application.

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
    errors({ stack: true }), // Log errors with stack trace
    logFormat
  ),
  transports: [
    new transports.Console(),
    new transports.File({ filename: 'combined.log' }),
    new transports.File({ filename: 'errors.log', level: 'error' }),
  ],
});

module.exports = logger;

```

### Integrating Winston with Express

Use the `winston` logger in your Express application to log HTTP requests and errors.

```javascript
// app.js
const express = require('express');
const morgan = require('morgan');
const bodyParser = require('body-parser');
const usersRouter = require('./routes/users');
const logger = require('./logger');

const app = express();

// Morgan logs all requests, using winston
app.use(morgan('combined', { stream: { write: message => logger.info(message.trim()) }}));

app.use(bodyParser.json());
app.use('/users', usersRouter);

// If no route matches
app.use((req, res, next) => {
  res.status(404).json({
    success: false,
    message: 'Resource not found',
  });
});

// Central error handler
app.use((err, req, res, next) => {
  logger.error(err.message, { stack: err.stack });
  res.status(err.status || 500).json({
    success: false,
    message: err.message || 'Internal Server Error',
  });
});

module.exports = app;

```

### Explanation

- **Using Morgan and Winston Together**: We use the `morgan` logging library with `winston`to log HTTP requests in detail and save them to a file.
- **Custom Log Format**: `winston` allows defining a custom log format that includes timestamps and error messages with stack trace.
- **Central Error Handler**:  We log errors using the `winston`  logger, which helps with error analysis later.
  
## Log Levels

`winston` has different log levels, which help categorize and filter logs:

- **error**: Error messages.
- **warn**: Warnings.
- **info**: Informational messages.
- **http**: HTTP request logging.
- **verbose**: More detailed messages.
- **debug**: SDebugging messages.
- **silly**: Very detailed messages.

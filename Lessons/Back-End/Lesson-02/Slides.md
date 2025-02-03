---
marp: true
---

# Web Development

## Back-End Development


---

## Today's Topics

- Recap of the previous lecture
- [Structuring - Controllers](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Back-End-Frameworks/Topics/Structuring/README.md#kontrollerid)
- Thunder Client
- [Sending Data to the API](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Back-End-Frameworks/Topics/Sending-Data-To-Express/README.md)
  - URL Parameters
  - Body
  - Query String

---

## What Did We Discuss in the Last Lecture?

---

## Structuring - Controllers

Controllers act as intermediaries between HTTP requests and responses and the application logic.

Controllers are typically responsible for the following tasks:

- Validating request data
- Routing the request
- Generating the response
- Error handling
- Security

---

## Example of Controllers

---

## Thunder Client

Some API requests (like `GET`) can be made directly from the browser, and it's convenient to do so. However, browser-based requests are limited, and not all types of requests can be made.

Thunder Client is a Visual Studio Code extension that allows you to make HTTP requests directly from the VS Code environment.

---

## Sending Data to the API

We have sent requests to APIs and used URL parameters to communicate our "intentions." However, there are other ways to send data:

- Request body (*req.body*)
- Request parameters (*req.query*)
- Headers (we will discuss later)

---

## Request Body (*req.body*)

Data sent in the request body is typically used in methods like POST, PUT, and DELETE. You can send data in the body that isn't practical to send as URL parameters, such as large texts, files, sensitive data, etc.

We usually send data in the request body in JSON format.

---

## Request Body (*req.body*) - Middleware Setup

By default, the `req` object in Express does not have the `body` property, where the request body is typically stored. To enable this, we need to use Express middleware.

```javascript
const express = require('express');
const app = express();

const port = 3000;

app.use(express.json()); // To read data in JSON format
app.use(express.urlencoded({ extended: true })); // To read data in URL encoded format
```
---

## PRequest Parameters(*req.query*)

You can send data via the URL using query parameters. For example, to send a search query, you can use a URL like `/search?q=example`. In an Express application, you can access query parameters using the `req.query` object. Query parameters are part of the URL starting with a question mark and follow the format `name=value`. They are commonly used for sending data related to the request's purpose, such as search terms or filter parameters.

---

## Query Parameters (req.query) - Example

```javascript
app.get('/search', (req, res) => {
  const query = req.query.q;
  res.send(`Search query: ${query}`);
});
```

---

## Homework

- Separate controllers and services in your API project into different files.
- Add the ability to create new data in your API using POST requests (for all resources).
- Install the Docker Desktop application on your computer.

---

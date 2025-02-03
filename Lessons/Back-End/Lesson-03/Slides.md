---
marp: true
---

# Web Development

## Back-End Development

Martti Raavel

<martti.raavel@tlu.ee>

---

## Today's Topics

- Recap of the previous lecture
- Review
  - [Structuring](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Back-End-Frameworks/Topics/Structuring/README.md)
    - Revisiting Services and Controllers
  - [Sending Data to the API](https://github.com/FE-BE-Microdegrees/Subjects/tree/main/Back-End-Frameworks/Topics/Sending-Data-To-Express/README.md)
    - `req.params`
    - `req.body`
    - `req.query`

---

## What Did We Discuss in the Last Lecture?

---

## Review

---

## Structuring

- **Services** - Logic responsible for data processing
- **Controllers** - Responsible for handling requests and sending responses

---

## Sending Data to the API

- `req.params`
- `req.body`
- `req.query`

---

## URI Parameters (*req.params*)

You can send data via the URL using URL parameters. For example, to send a product ID, you might use the URL `/products/:id`. In Express, you can access the URL parameter using the `req.params` object.

---

## `req.params` Example

```javascript
...
app.get('/users/:id', (req, res) => {
  const userId = req.params.id;
  res.send(`User ID: ${userId}`);
});
...
```
> If you use the URI `/users/123`, the `req.params` object will look like `{ id: '123' }`.

---

Request Body (req.body)

You can send data in the request body using methods like POST, PUT, and DELETE. Data is usually sent in `JSON` or `form` format. To access the request body in an Express app, you need to register middleware:

```javascript
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
```

---

## `req.body` Example

```javascript
...
app.post('/students/add', (req, res) => {
  const student = req.body;
  console.log(student);
});
...
```

If you send a request to `/students/add` with the following body:

```json
{
  "firstName": "Angus",
  "lastName": "Ingram",
  "curriculum": "RIF22"
}
```

then the `req.body` object will look like:
`{ firstName: 'Angus', lastName: 'Ingram', curriculum: 'RIF22' }`.

---

## Query Parameters (req.query)

Query parameters allow you to send data through the URL. For example, to send a search query, you could use the URL  `/search?q=example`. In an Express app, you can access the query parameters using the `req.query` object.


---

## `req.query` Example

Sending a request to  `/search?q=example`, you can retrieve the query parameters with the following code:

```javascript
...
app.get('/search', (req, res) => {
  const query = req.query.q; // 'example'
  res.send(`Search query: ${query}`);
});
...
```

> In this example, the `req.query` object will contain : `{ q: 'example' }`.

---

## Middleware

`Middleware` functions are functions that have access to the request object (`req`), the response object (`res`), and the next function in the application's request-response cycle.
---

## Next funktsioon

The `Next` function is a part of the Express router and, when invoked, passes control to the next middleware function in the stack.

Essentially, it allows you to move to the next step in the application's request-response cycle.
---

## Middleware Example

```javascript
// Middleware for logging HTTP requests to the console

const logger = (req, res, next) => {
  // Log the request URL, method, and timestamp
  console.log(req.url, req.method, new Date().toISOString());
  // Invoke the next middleware function
  return next();
}
```

---

## Registering Middleware

You can apply `Middleware` in different ways.

One way is to register `middleware` for all routes:

```javascript
...
// Import middleware (path depends on file location)
const logger = require('./middlewares/logger');
...
// Register middleware
app.use(logger);
...
```

---

## Registering Middleware for Specific Routes

Another way is to register `middleware` for specific routes:

```javascript
...
// Import middleware
const logger = require('./middlewares/logger');
...
// Register middleware
app.get('/api', logger, (req, res) => {
  res.send('Hello World!');
});
...
```

---

## Homework

- Install Docker Desktop on your computer.
- Add the ability to create new resources to your project (if not already added).
- Add validation to resource creation to ensure that users cannot submit empty or invalid data.

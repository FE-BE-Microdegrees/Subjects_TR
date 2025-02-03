---
marp: true
---

# Web Development

## Back-End Development

Martti Raavel

<martti.raavel@tlu.ee>

---

## Today's Topics

- Review of the previous lecture
- [Middleware](https://github.com/FE-BE-Microdegrees/Subjects/blob/main/Back-End-Frameworks/Topics/Middleware/README.md)
- [Express Router](https://github.com/FE-BE-Microdegrees/Subjects/blob/main/Back-End-Frameworks/Topics/Routes/README.md)

---

## What Did We Discuss in the Previous Lecture?

---

## Middleware

`Middleware` functions are functions that have access to the request object (`req`), response object (`res`), and the next function in the application's request-response cycle.

---

## Middleware

In essence, `middleware` can be thought of as a filter that processes requests before they reach the next stage in the request-response cycle.

---

## Using Middleware

`Middleware` can:

- Execute code
- Make changes to request and response objects
- End the request-response cycle
- Call the next middleware in the queue
- ...

---

## Registering Middleware

`Middleware` can be applied:

- To all requests
- To specific routes only
- ...

---

## The `Next` Function

The `next` function is an Express function that, when called, passes control to the next `middleware` function in the chain.

---

## Middleware Example

```javascript
// Middleware to log HTTP requests to the console

const logger = (req, res, next) => {
  // Logs request target, method, and time
  console.log(req.url, req.method, new Date().toISOString());
  // Calling the next function passes control to the next middleware
  return next();
}
```
---

## Registering  `Middleware` for All Requests

```javascript
...

// Registering Middleware
app.use(logger);

...
```

---

## Registering `Middleware` for Specific Routes Only

```javascript
...

// Registering Middleware
app.get('/api', logger, (req, res) => {
  res.send('Hello World!');
});

...
```

---

## Not Found middleware

One possible use of `middleware`is to display a 404 page if the requested resource cannot be found.

---

## Not Found middleware näide

```javascript
// Displaying a 404 page if the requested resource is not found

const notFound = (req, res, next) => {
  res.status(404).send({
    success: false,
    message: 'Not Found'
  });
}
```

---

## Registering Not Found  middleware 

```javascript

// Importing Middleware
const notFound = require('./middlewares/notFound');

...

// Registering Middleware
app.use('*', notFound);

...
```

---

## Express Router

`Router` is an object in the `Express` framework that allows us to group routes.

---

## Using Express Router

To use Express Router, we first create a separate file for each resource and write the routes for that resource.

---

## Express Router Example

```javascript
// Routes related to cars

const express = require('express');
const router = express.Router();

const carsControllers = require('./carsControllers');


router.get('/', carsControllers.getAll);
router.get('/:id', carsControllers.getById);
router.post('/', carsControllers.create);

module.exports = router;
```

---

## Importing and Using Express Router

The `Router` object can be used in an `Express` application by using the `app.use` method.

```javascript

// Importing Router

const carsRoutes = require('./cars/carsRoutes');

...

// Using Router

app.use('/cars', carsRoutes);

...
```

---

## Homework

- Read through the materials for Lecture Four:
  - [Middleware](https://github.com/FE-BE-Microdegrees/Subjects/blob/main/Back-End-Frameworks/Topics/Middleware/README.md)
  - [Express Router](https://github.com/FE-BE-Microdegrees/Subjects/blob/main/Back-End-Frameworks/Topics/Routes/README.md) materjalid
- Structure your project's routes as `Router` objects
- Add a `middleware` function to your project that logs all requests with the timestamp to the console
- Install [Docker Desktop](https://www.docker.com/products/docker-desktop/) on your computer

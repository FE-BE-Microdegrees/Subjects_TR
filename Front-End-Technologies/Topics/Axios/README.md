# Axios: JavaScript HTTP Client

In this guide, we introduce the Axios library, a popular JavaScript HTTP client used for making asynchronous requests to web servers. Axios provides a simple API for performing HTTP requests, making it easier to send and receive data.

## Learning Outcomes

By the end of this topic, you will be able to:

- Explain what Axios is and why it is used;
- Set up Axios in your projects;
- Use the Axios library for HTTP requests.

## What is Axios?

Axios is a promise-based HTTP client for JavaScript, designed for sending and receiving data from web servers. It supports both browser and Node.js environments, making it a versatile choice for various development scenarios.

## Why Use Axios?

Axios offers several advantages:

- **Promise-Based API**: Axios uses JavaScript Promises, simplifying the handling of asynchronous operations.
- **Request Cancellation**: Axios allows you to cancel HTTP requests, useful for long-running or unnecessary requests.
- **Request and Response Interception**: Axios enables modifying requests before they are sent and responses before they are processed.
- **Automatic Data Transformation**: Axios automatically transforms request data to JSON and parses JSON responses.

## Setting Up Axios with Async/Await

Before using Axios, make sure it is included in your project:

### Using CDN (In the Browser)

Include Axios via a script tag in your HTML files:

```html
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
```

### Using NPM or Yarn

For Node.js projects or if using a module bundler:

```bash
npm install axios
```

Then, import it into your JavaScript file:

```javascript
const axios = require('axios');
```

## Examples of Using Axios with Async/Await

### GET Request

An example of performing a GET request and handling the response using async/await:

```javascript
async function fetchUsers() {
  try {
    const response = await axios.get('https://jsonplaceholder.typicode.com/users');
    console.log(response.data);
  } catch (error) {
    console.error('Error with request:', error);
  }
}

fetchUsers();

```

### POST Request

An example of sending data to a server with a POST request using async/await:

```javascript
async function createUser(userData) {
  try {
    const response = await axios.post('https://jsonplaceholder.typicode.com/users', userData);
    console.log('User created:', response.data);
  } catch (error) {
    console.error('Error creating user:', error);
  }
}

const userData = {
  name: 'John Doe',
  email: 'john@example.com'
};

createUser(userData);

```

### Sending Headers with Axios

Often, we want to include headers with requests to APIs, such as an authentication token. Here's how to send headers using Axios:

```javascript
async function fetchUser(userId) {
  try {
    const response = await axios.get(`https://jsonplaceholder.typicode.com/users/${userId}`, {
      headers: {
        Authorization: 'Bearer my-auth-token'
      }
    });
    console.log(response.data);
  } catch (error) {
    console.error('Error with request:', error);
  }
};

fetchUser(1);
```

## Summary

Axios combined with async/await provides a clean and manageable way to perform HTTP requests. This combination improves code readability and reduces errors in asynchronous operations. Using these tools together, you can optimize data exchange in web applications.

## Sources

- Axios GitHub leht: [Axios GitHub](https://github.com/axios/axios)
- MDN Web Docs, async ja await: [Asynchronous Programming](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous)

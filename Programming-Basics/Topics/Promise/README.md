# Promise

![Promise](Promise.webp)

- [Promise](#promise)
  - [Learning Outcomes](#learning-outcomes)
  - [What is a *Promise*?](#what-is-a-promise)
  - [Why use *Promise*?](#why-use-promise)
  - [Example](#example)

## Learning Outcomes

After completing this topic, you will be able to:

- Define what a *Promise* is;
- Explain why *Promise* is used;
- Use *Promise* to handle asynchronous operations.

## What is a *Promise*?

A *Promise* is an object that represents the eventual completion or failure of an asynchronous operation. Essentially, a *Promise* is a returned object to which you can attach [*Callback*](../callback/README.md) functions, rather than passing them as arguments to a function.

## Why use *Promise*?

*Promise* provides a way to handle asynchronous operations, such as fetching data from an API, reading files, or other long-running tasks, without blocking the main thread.

A *Promise* object has three states:

1. Pending: The initial state of the *promise*, meaning it is neither fulfilled nor rejected.
2. Fulfilled: The state when the asynchronous operation is successfully completed, and the promised value is available.
3. Rejected: The state when the asynchronous operation fails, and the promised value is not available.

Promises are created using the `Promise` constructor. The constructor takes a function containing asynchronous code (e.g., an API request) and returns a *Promise* object. This function, in turn, expects two arguments: `resolve` and `reject`. The `resolve` function is called if the asynchronous operation is successful, and `reject` is called if it fails.

Creating a *Promise* looks like this:

```javascript
const promise = new Promise((resolve, reject) => {
  // Asynchronous operation
  const result = callToExternalAPI();

  if (result) {
    // Operation successful
    resolve(result);
  } else {
    // Operation failed
    reject("Error occurred");
  }
});
```

Once a Promise is created, you can handle its fulfilled state using the .then() method and its rejected state using the .catch() method. The .then() method takes a function as an argument, which executes with the value returned by the successful operation. Similarly, the .catch() method takes a function as an argument, which executes with the error message returned by the failed operation.

For example:

```javascript
promise
  .then((result) => {
    console.log(result); // Handle fulfilled state
  })
  .catch((error) => {
    console.error(error); // Handle rejected state
  });

```

## Example

Suppose we have an application that fetches data from an API. We can use Promise to handle the data retrieval. Here’s an example:

```javascript
const axios = require('axios'); // Axios is an HTTP client for making API requests

const url = 'https://jsonplaceholder.typicode.com/posts/1'; // API URL

const promise = new Promise((resolve, reject) => { // Create a new Promise object
  const result = axios.get(url); // Make an API request
  if (result) { // If the request is successful
    resolve(result); // Call the resolve function
  } else {
    reject('Error'); // Call the reject function
  }
});

promise
  .then((response) => { // Handle the Promise
    console.log(response.data); // Display the API response
  })
  .catch((error) => { // Handle rejection
    console.log(error); // Display the error message
  });

console.log('End');

```

When this code runs, the console displays the following output:

```bash
End
{
  userId: 1,
  id: 1,
  title: 'sunt aut facere repellat provident occaecati excepturi optio reprehenderit',
  body: 'quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto'
}

```

*Promise* objects are a vital part of handling asynchronous operations in JavaScript. However, understanding how they work can be challenging at first. Now, with the introduction of async/await, their usage and readability have become more straightforward.

Sources:

- <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise>
- <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises>

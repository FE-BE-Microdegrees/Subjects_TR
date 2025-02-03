# Async/Await

![Async Await](Async-Await.webp)

Image Source: [Dall-E by OpenAI](https://openai.com/)

- [Async/Await](#asyncawait)
  - [Learning Outcomes](#learning-outcomes)
  - [What is `async/await`?](#what-is-asyncawait)
  - [Why Use `async/await`?](#why-use-asyncawait)

## Learning Outcomes

After completing this topic, you will be able to:

- Explain what `async/await` is
- Understand why `async/await` is used
- Use `async/await` in JavaScript

## What is `async/await`?

`async/await` is a feature of modern JavaScript that allows you to write asynchronous code in a way that looks and behaves like synchronous code. It is essentially a syntactic improvement built on top of [*promises*](../promise/README.md) to simplify their usage.

## Why Use `async/await`?

The `async` keyword is used to define an asynchronous function. Such a function always returns a *promise*, which can have three states:

1. Pending
2. Fulfilled
3. Rejected

For example:

```javascript
const url = 'https://jsonplaceholder.typicode.com/posts/1'; // API URL

async function fetchData() {
  const response = await fetch(url);
  const data = await response.json();
  return data;
}
```

The `await` keyword pauses the execution of the function until the promise is fulfilled or rejected. Once the promise is resolved, it returns the resulting value and resumes the function execution. If the promise is rejected, an exception is thrown, which can be caught using a `try/catch` block.

```javascript
async function main() {
  try {
    const data = await fetchData(); // Waits for fetchData to resolve
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

main();

```

In the example above, the main asynchronous function fetches data using the fetchData function. The execution of main pauses while waiting for fetchData to complete. If the fetchData call succeeds, the fetched data is logged to the console. If it fails, the error is caught in the catch block and displayed in the console

> Note: The  `await` keyword can only be used inside functions defined with the `async` keyword.

As seen in the example, the use of `async/await` provides a clearer and more readable syntax compared to usingi *promise* alone.

Sources:

- <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function>

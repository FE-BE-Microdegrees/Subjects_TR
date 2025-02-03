---
marp: true
---

# Software Development and Programming



---

## Software Development

- Recap of the previous lecture
- ESLint + Airbnb
  - [ESLint + Airbnb](https://github.com/FE-BE-Microdegrees/Subjects/blob/Lesson-translation/Software-Development/Topics/ESLint/README.md)

---

## Recap of the Previous Lecture

---

## ESLint - What?

ESLint is a popular open-source tool for static code analysis of JavaScript code. It is used to find and fix common coding problems and to enforce a consistent coding style across the project.

---

## Airbnb Style Guide

The Airbnb style guide is one of the most popular JavaScript style guides. It is a widely adopted style guide based on best practices, aiming to promote code consistency and maintainability. The Airbnb JavaScript style guide is maintained by the Airbnb team and is used by many developers and organizations worldwide.

---

## Installing ESLint for a NodeJS Project (VSCode) - Extension

First, add the ESLint extension to VSCode (if it’s not already added). You can find it under extensions or here: <https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint>

---

## Installing ESLint for a NodeJS Project (VSCode) - Dev Dependency

Install ESLint as a development dependency as follows:

```bash
npm install eslint --save-dev
```
Run ESLint setup from your project root:

```bash
npx eslint --init
```

Answer the setup questions.

---

## Programming

- [Nodemon Module](../../../Subjects/Programming-Basics/Topics/Nodemon/README.md)
- Synchronous and Asynchronous Code
  - [callback](../../../Subjects/Programming-Basics/Topics/Callback/README.md)
  - [async/await](../../../Subjects/Programming-Basics/Topics/Async-Await/README.md)
- [Try/Catch](../../../Subjects/Programming-Basics/Topics/Try-Catch-Finally/README.md)
- [File Reading and Writing (`fs` module)](../../../Subjects/Programming-Basics/Topics/Modules-Built-In/README.md#fs-moodul)
- [JSON.stingify()](../../../Subjects/Programming-Basics/Topics/JSON/README.md#jsonstringify)

---

## Nodemon - What?

Nodemon is a utility that helps developers automate the development process of Node.js applications. Nodemon monitors your project files for changes and automatically restarts the Node.js application when it detects changes.

---

## Installing Nodemon

You can install Nodemon globally or as a development dependency. I recommend installing it as a development dependency.

```bash
npm install nodemon --save-dev
```

---

## Using Nodemon

Run your Node.js application with Nodemon as follows:

```bash
nodemon app.js
```

---

## Nodemon - Info

It seems that Nodemon doesn’t work well with the  `prompt-sync` module.

---

## Synchronous vs Asynchronous

What does asynchronous mean in JavaScript?

---

## Asynchronous Code

Asynchronous code is code that does not block the main thread. Asynchronous code allows multiple asynchronous operations to occur simultaneously, without waiting for one operation to complete before starting another.

---

## Synchronous Code

Synchronous code is code that blocks the main thread. Synchronous code is executed sequentially, one line at a time. When one line is completed, the next line is executed.

---

## Asynchronous - How to Handle It?

- Callback
- Async/Await

---

## Callback - What?

A callback is a function that is passed as an argument to another function and is executed when the first function has completed its task.

---

## Callback - Example

```js
function callbackExample() {
  console.log("Callback function has been called!");
}

function greet(name, callback) {
  console.log("Hello, " + name + "!");
  callback();
}

greet("John", callbackExample);
```

---

## Async/Await - What?

`async/await` is a modern JavaScript feature that allows writing asynchronous code in a way that looks and behaves like synchronous code.

`async` and `await` make reading and writing asynchronous code easier.

---

## Async/Await - States

The `async` keyword is used to define an asynchronous function. Functions defined this way always return a promise, which can have three states:

1. Pending
2. Fulfilled
3. Rejected

---

## Async/Await - Example

```js
const url = "https://jsonplaceholder.typicode.com/posts/1"; // API URL

async function fetchData() {
  const response = await fetch(url);
  const data = await response.json();
  return data;
}
```

---

## Async/Await - What Happens When Something Goes Wrong?

---

## Try/Catch - What?

The `try...catch` statement is a JavaScript construct used for error handling. It allows us to attempt (try) to execute code that might cause an error, and if an error occurs, we can catch it and handle it.

The `try...catch` statement is useful because it helps prevent programs from crashing due to errors. It allows handling errors that occur during program execution, enabling the program to continue despite encountering errors that NodeJS would otherwise be unable to handle without stopping execution.

---

## Try/Catch - Example

```js
async function main() {
  try {
    const data = await fetchData(); // Waits for fetchData function to complete
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
```

---

## `fs` Module

The `fs` module is a built-in NodeJS module that allows reading and writing files. With this module, you can perform almost any file-related operation—reading, writing, modifying, deleting, etc.

---

## Reading a File

```js
const fs = require("fs");

fs.readFile("file.txt", "utf8", (error, data) => {
  if (error) console.log("An error occurred");
  console.log(data);
});

console.log("Reading file...");

```

---

## Writing a File

```js
const fs = require("fs");

fs.writeFile("file.txt", "Hello, World!", (error) => {
  if (error) console.log("Tekkis viga");
  console.log("File has been written!");
});
```

---

## Appending to a File

```js
const fs = require("fs");

fs.appendFile("file.txt", "Hello, World!", (error) => {
  if (error) console.log("Tekkis viga");
  console.log("Data has been appended to file!");
});
```

---

## `fs` Module Synchronously

---

## Reading a File Synchronously

```js
const fs = require("fs");

const data = fs.readFileSync("file.txt", "utf8");

console.log(data);
```

---

## What Happens if the File is Not Found?

---

## Handling Errors While Reading a File

```js
const fs = require("fs");

try {
  const data = fs.readFileSync("file.txt", "utf8");
  console.log(data);
} catch (error) {
  console.error(error);
}
```

---

## Writing a File Synchronously

```js
const fs = require("fs");

fs.writeFileSync("file.txt", "Hello, World!");

console.log("File has been written!");
```

---

## Appending to a File Synchronously

```js
const fs = require("fs");

fs.appendFileSync("file.txt", "Hello, World!");

console.log("Data has been appended to file!");
```

---

## Storing Objects and Arrays in Files

If we want to read and write objects and arrays to files, we must use the `JSON.stringify()` and `JSON.parse()` methods, otherwise they will be read and written as strings in the files.

---

## JSON - What?

JSON stands for JavaScript Object Notation and is a simple and readable data exchange format commonly used for exchanging data between client and server applications—for example, between the front-end of a web application and an API.

---

## JSON - Example

```json
{
  "name": "John",
  "age": 30,
  "isStudent": true,
  "favoriteFoods": ["pizza", "sushi", "ice cream"]
}
```

---

## JSON - Difference from JavaScript Object

A JSON object looks very similar to a JavaScript object, but it’s important to note that JSON is a data exchange format, not the JavaScript object itself. The main difference is that JSON keys are always enclosed in quotes, whereas keys in JavaScript objects are usually not.

---

## JSON vs JavaScript Object - Example

```json
{
  "name": "John",
  "age": 30,
  "isStudent": true,
  "favoriteFoods": ["pizza", "sushi", "ice cream"]
}
```

```js
const person = {
  name: "John",
  age: 30,
  isStudent: true,
  favoriteFoods: ["pizza", "sushi", "ice cream"],
};
```

---

## `JSON.stringify()`

`JSON.stringify()` is a JavaScript function that converts a JavaScript object into a JSON string. It takes an object as input and returns it as a JSON string.

---

## `JSON.stringify()` - Example

```js
const person = {
  name: "John",
  age: 30,
  isStudent: true,
  favoriteFoods: ["pizza", "sushi", "ice cream"],
};

const jsonPerson = JSON.stringify(person);

console.log(jsonPerson);
```

Output:

```json
{
  "name": "John",
  "age": 30,
  "isStudent": true,
  "favoriteFoods": ["pizza", "sushi", "ice cream"]
}
```

---

## `JSON.parse()`

`JSON.parse()` is a JavaScript function that converts a JSON string into a JavaScript object. It takes a JSON string as input and returns it as a JavaScript object.

---

## `JSON.parse()` - Example

```js
const jsonPerson =
  '{"name":"John","age":30,"isStudent":true,"favoriteFoods":["pizza","sushi","ice cream"]}';
const person = JSON.parse(jsonPerson);

console.log(person);
```

Output:

```js
{
  name: 'John',
  age: 30,
  isStudent: true,
  favoriteFoods: [ 'pizza', 'sushi', 'ice cream' ]
}
```


# Jest Testing Framework

## Introduction

Jest is a popular and powerful testing framework used primarily for testing JavaScript and React projects. It provides rich functionality to write and execute unit, integration, and end-to-end tests. Designed to be simple and user-friendly, Jest includes built-in features like mocking and test environments.

---

## Learning Outcomes

By the end of this tutorial, learners should be able to:

- Explain what Jest is and why it is used.
- Install and configure Jest for testing.
- Write and execute basic tests using Jest.
- Utilize Jest's built-in features like mocking and test environments.

---

## What is Jest?

Jest is a JavaScript testing framework created by Facebook. It is ideal for testing React applications but is versatile enough to be used for other JavaScript projects as well. Jest offers built-in functionalities such as mocking, temporary environments, and extensibility.

### Advantages of Jest

- **All-in-One Solution:** Jest includes everything needed for testing without requiring additional tools.
- **Easy Setup:** Jest is simple to set up and use.
- **Performance:** Jest can run tests in parallel, making testing fast and efficient.
- **Built-in Mocking:** Jest includes native support for mocking, simplifying complex test writing.

---

## Installing and Setting Up Jest

### 1. Install Jest

Install Jest as a dev dependency in your project:

```bash
npm install --save-dev jest
```

Or, if using Yarn:

```bash
yarn add --dev jest
```

### 2. Add Script to `package.json` 

Add a script to run Jest tests:

```json
{
  "scripts": {
    "test": "jest"
  }
}
```

### 3. Create a Test File

Create a directory named `__tests__`  in the root of your project and add a test file, e.g.,  `sum.test.js`.

```bash
mkdir __tests__
cd __tests__
touch sum.test.js
```

## Writing Tests with Jest

### Example: Basic Test

#### `sum.js` - Function to be Tested

```javascript
function sum(a, b) {
  return a + b;
}

module.exports = sum;
```

#### `__tests__/sum.test.js` - Jest Test

```javascript
const sum = require('../sum');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});

test('adds -2 + 1 to equal -1', () => {
  expect(sum(-2, 1)).toBe(-1);
});
```

### Running Tests

Run tests using the Jest command:

```bash
npm test
```

## Testing Asynchronous Code

Jest supports asynchronous tests using callbacks, promises, o `async`/`await` .

### Example: Testing Promises

#### `asyncFunction.js` - Asynchronous Function

```javascript
function asyncFunction() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve('Hello World');
    }, 1000);
  });
}

module.exports = asyncFunction;
```

#### `__tests__/asyncFunction.test.js` - Jest test

```javascript
const asyncFunction = require('../asyncFunction');

test('async function returns "Hello World" after 1 second', () => {
  return asyncFunction().then(data => {
    expect(data).toBe('Hello World');
  });
});
```

### Example: Using `async`/`await`

#### `__tests__/asyncFunctionAsync.test.js` - Jest test

```javascript
const asyncFunction = require('../asyncFunction');

test('async function returns "Hello World" after 1 second', async () => {
  const data = await asyncFunction();
  expect(data).toBe('Hello World');
});
```

## Mocking with Jest

Jest provides built-in support for mocking modules and functions to test code in isolation.

### Example: Mocking a Function

#### `fetchData.js` - Function to be Tested

```javascript
const axios = require('axios');

async function fetchData() {
  const response = await axios.get('https://api.example.com/data');
  return response.data;
}

module.exports = fetchData;
```

#### `__tests__/fetchData.test.js` - Jest Test with Mocking

```javascript
const fetchData = require('../fetchData');
const axios = require('axios');

jest.mock('axios');

test('fetches data from API', async () => {
  const data = { name: 'John Doe' };
  axios.get.mockResolvedValue({ data });

  const result = await fetchData();
  expect(result).toEqual(data);
});
```

## Test Environment with Hooks

Jest provides hooks like (`beforeEach`, `afterEach`, `beforeAll`, `afterAll`) to execute code before and after tests.

### Example: Using Hooks

```javascript
let data;

beforeAll(() => {
  data = { name: 'John Doe' };
});

afterAll(() => {
  data = null;
});

test('data name is John Doe', () => {
  expect(data.name).toBe('John Doe');
});
```

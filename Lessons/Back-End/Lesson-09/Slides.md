# Web Development

## Back-End Development


---

## Today's Topics

- Review of the previous lecture
- [Automated Testing of Node API](https://github.com/FE-BE-Microdegrees/Subjects/blob/Lesson-translation/Back-End-Frameworks/Topics/Testing/README.md)

---

## What Did We Cover in the Previous Lecture?

---

## Automated Testing for Express API

---

## Testing

Testing is the process of evaluating the quality of software by examining its functionality, performance, and security. The goal of testing is to identify bugs and issues and confirm that the software works as expected and meets defined requirements.

---

## Types of Testing

- Unit Testing
- Integration Testing
- System Testing
- Acceptance Testing
- etc.

---

## Testing Methods

- Manual Testing
- Automated Testing

---

## Node.js Testing Frameworks

- Mocha
- Jest
- SuperTest
- etc.

---

## Mocha

Mocha is a flexible and simple testing framework for Node.js that allows you to write and run tests.

---

## Installing and Using Mocha

```bash
npm install mocha
```

Create a folder named `test` in the project root and add a test file, for example, `test.js`.

> By default, Mocha looks for test files in the  `test` folder.
>
> Going forward, you can name test files like `resource.test.js`.

---

## Adding a Script to `package.json` 

```json
{
  "scripts": {
    "test": "mocha --exit"
  }
}
```

> Tests can now be run from the command line using `npm test`.

---

## Structure of Mocha Tests

Mocha uses functions `describe`, `it`, `before`, `after`, `beforeEach`, `afterEach` to write tests in BDD style..

The `describe` function allows you to group and describe tests.

The `it` function describes individual tests.

---

## Example Structure of Mocha Tests

```javascript
describe('Test Group Name', function() {
  it('Test Description', function() {
    // Test code
  });
  it('Test Description', function() {
    // Test code
  });
});

```

---

## Example Mocha Tests

```javascript
const assert = require('assert');
const sum = require('./sum');

describe('sum', () => {
  it('should return 3 when the input is 1 and 2', () => {
    assert.strictEqual(sum(1, 2), 3);
  });

  it('should return 5 when the input is 2 and 3', () => {
    assert.strictEqual(sum(2, 3), 5);
  });

  it('should return 0 when the input is 0 and 0', () => {
    assert.strictEqual(sum(0, 0), 0);
  });
});

```

> `assert` is a standard Node.js module that allows you to make assertions.

---

## Chai

Chai is a popular assertion library for JavaScript that is used with testing frameworks like Mocha and Jest.

---

## Installing Chai

```bash
npm install chai@4.4.1
```

> Note: We use Chai version 4.4.1 as it is the last version that supports Node.js `require` syntax.

---

## Using Chai

```javascript
it('should return 3 when the input is 1 and 2', () => {
  expect(sum(1, 2)).to.equal(3);
});
```

---

## Chai Assertion Styles

- `expect`
- `should`
- `assert`

Chai cheatsheet: <https://devhints.io/chai>

---

## Expect Assertion Style

```javascript
expect(object)
  .to.equal(expected)
  .to.deep.equal(expected)
  .to.be.a('string')
  .to.include(val)
  .be.ok(val)
  .be.true
  .be.false
  .to.exist
  .to.be.null
  .to.be.undefined
  .to.be.empty
  .to.be.arguments
  .to.be.function
  .to.be.instanceOf
  .to.have.property
```

---

## SuperTest

SuperTest is a Node.js framework that enables testing of HTTP requests and responses.

---

## Advantages of SuperTest Over Other Frameworks

- Easy integration
- No need to start the server
- Rich query options
- Readable assertions
- Supports asynchronous tests

---

## Installing SuperTest

```bash
npm install supertest
```

---

## Using SuperTest

```javascript
const request = require('supertest');
const app = require('../app');
const { expect } = require('chai');
const { describe, it } = require('mocha');

describe('GET /ping', function() {
  it('responds with json', function(done) {
    request(app)
      .get('/')
      .set('Accept', 'application/json')
      .expect('Content-Type', /json/)
      .expect(200, done);
  });
});
```

---

## Preparation

Before we can start writing tests for our application, we need to structure our application a bit more. To enable automated testing of the API, we need to separate the code that creates the API from the code that starts the server.
---

## Structuring

Create a separate file named`server.js`in the project root, and move the code that starts the server from `app.js` 
```javascript
const app = require('./app');

app.listen(3000, () => {
  console.log('Server is running on http://localhost:3000');
});
```

This means that `app.js` only contains code to create the API, which is then exported.

---

## Writing SuperTest Tests

```javascript
const request = require('supertest');
const { expect } = require('chai');
const { describe, it } = require('mocha');

const app = require('../app');

const okResponse = {
  success: true,
  message: 'pong',
};

describe('GET /ping', () => {
  it('should return 200 OK', async () => {
    const response = await request(app).get('/ping');
    expect(response.status).to.equal(200);
    expect(response.body).to.deep.equal(okResponse);
  });
});
```

---

## Testing Requests That Require Login

Just like when testing manually, for automated tests, we need to send login credentials to test requests that require authentication.

```javascript
const request = require('supertest');
const { expect } = require('chai');
const { describe, it, before } = require('mocha');
let token;

// Login

before(async () => {
  const response = await request(app)
    .post('/login')
    .send(user);
  token = response.body.token;
});

// Testing Requests That Require Login

it('should return 200 OK', async () => {
  const response = await request(app)
    .get('/protected')
    .set('Authorization', `Bearer ${token}`);
  expect(response.status).to.equal(200);
});

```

---

## Tests and Database
Currently, we run tests using the real database. This is bad practice because tests can modify the database, and the database can affect test results.

It’s reasonable to create a separate database for testing, which is used only for tests. This database should be created each time tests are run and deleted afterward. This allows us to write tests knowing exactly what data is in the database and the expected responses for queries.
---

## Environment Variables

We need a way for the application to distinguish between testing and non-testing modes. We can use the environment variable `NODE_ENV`with values of `test` or `development`.

Environment variables are variables set in the operating system environment that can be used to affect application behavior.

Environment variables can be used in applications in various ways:

- `.env` files
- Command-line arguments
- Operating system environment variables
- ...

---

## Using Environment Variables

To read environment variables, we install the Node.js module `dotenv`.

```bash
npm install dotenv
```

---

## Database Configuration

Update the `config.js` file so that the settings used by the application depend on the environment variable.

```javascript
require('dotenv').config();

const config = {
  development: {
    port: 3000,
    jwtSecret: 'my-secret-key',
    saltRounds: 10,
    db: {
      host: 'localhost',
      ...
    },
  },
  test: {
    port: 3000,
    jwtSecret: 'my-secret-key',
    saltRounds: 10,
    db: {
      host: 'localhost',
      ...
    },
  },
};

const env = process.env.NODE_ENV || 'development'

module.exports = config[env];
```

---

## Modifying the `package.json` Script

Now that we can use environment variables, let’s modify the test script so that before running the tests, it sets the environment variable `NODE_ENV` to `test`. Remember that different operating systems use different syntax for setting environment variables. To avoid compatibility issues, we use the Node.js module `cross-env`.

```bash
npm install cross-env
```

And modify the test script as follows:

```json
{
  "scripts": {
    "test": "cross-env NODE_ENV=test mocha --exit"
  }
}
```

---

## Adding a Test Database

We now need to create a separate test database, add data, create the database at the start of the tests, and delete it after the tests finish.

The easiest way to do this is to create a separate `docker` **container as we did previously—just keep in mind that the test and** `real` databases need to use different ports.

---

## Test Database Setup

In addition, create a separate file testDbSetup.js for setting up the test database and populating it with data.

This file imports the SQL file created for the test database, splits it into individual queries, and adds them to the database

---

## Enhancing Tests

Now, we add database setup before running tests:

```javascript
const { setupTestDatabase } = require('../testDbSetup');

before(async () => {
  await setupTestDatabase();
});
```

> After tests, we do not delete the database since it’s recreated each time tests are run.

---

## Test Coverage

It’s useful to know the percentage of our application code covered by tests. For this, we use a tool like `nyc`.

```bash
npm install nyc
```

Enhance the test script as follows:

```json
{
  "scripts": {
    "test": "cross-env NODE_ENV=test nyc mocha --exit"
  }
}
```

This will show the test coverage percentage when running the tests.

---

## Homework

Try to add as many tests as possible to your API

# Node API Testing with Supertest, Mocha, and Chai: Running and Testing the Application

API testing is essential to ensure your application's endpoints function correctly. In this guide, we will set up and test a Node.js API using Express with Supertest, Mocha, and Chai. We'll first separate the Express application logic and server startup into different files (`app.js` and `server.js`) to simplify testing. Then, we'll create and execute tests to validate the API endpoints.

---

## Learning Objectives

By the end of this tutorial, learners will be able to:

- Configure the Express application and server startup in separate files.
- Test API endpoints using Supertest, Mocha, and Chai.
- Check test coverage using the `nyc` tool.

---

## Project Structure

```plaintext
my-blog-api/
│
├── app.js          # Express application configuration
├── server.js       # Server startup
├── routes/
│   └── posts.js    # API endpoints
├── controllers/
│   └── postsController.js  # Controllers for endpoints
└── services/
    └── postsService.js     # Services for business logic
└── test/
    └── posts.test.js       # Tests for API endpoints
└── package.json    # Project configuration and dependencies
```

## API Setup

### `app.js`

Set up the Express application and routes. This file contains the application logic and configuration without starting the server.

```javascript
const express = require('express');
const postsRouter = require('./routes/posts');

const app = express();

// Middleware for parsing JSON requests
app.use(express.json());

// Use routes for posts endpoints
app.use('/posts', postsRouter);

module.exports = app;

```

### `server.js`

Start the server by importing the application from `app.js` and listening on a specified port.

```javascript
const app = require('./app'); // Import the Express application
const PORT = process.env.PORT || 3000;

// Start the server
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

### `routes/posts.js`

Define API endpoints and link them to controllers in `postsController.js`.

```javascript
const express = require('express');
const router = express.Router();
const postsController = require('../controllers/postsController');

// Define endpoints and link to controllers
router.get('/', postsController.getAllPosts);
router.post('/', postsController.createPost);
router.put('/:id', postsController.updatePost);
router.delete('/:id', postsController.deletePost);

module.exports = router;
```

### `controllers/postsController.js`

Controllers handle HTTP requests and responses, delegating logic to services in`postsService.js`.

```javascript
const postsService = require('../services/postsService');

// Retrieve all posts
exports.getAllPosts = (req, res) => {
  const posts = postsService.getAllPosts();
  res.json(posts);
};

// Create a new post
exports.createPost = (req, res) => {
  const newPost = postsService.createPost(req.body);
  res.status(201).json(newPost);
};

// Update an existing post
exports.updatePost = (req, res) => {
  const updatedPost = postsService.updatePost(parseInt(req.params.id), req.body);
  if (updatedPost) {
    res.json(updatedPost);
  } else {
    res.status(404).send('Post not found');
  }
};

// Delete a post
exports.deletePost = (req, res) => {
  const deleted = postsService.deletePost(parseInt(req.params.id));
  if (deleted) {
    res.status(204).send();
  } else {
    res.status(404).send('Post not found');
  }
};

```

### `services/postsService.js`

Services handle business logic and data operations.

```javascript
let posts = [
  { id: 1, title: 'First Post', content: 'This is the first post' },
  { id: 2, title: 'Second Post', content: 'This is the second post' }
];

// Retrieve all posts
exports.getAllPosts = () => posts;

// Create a new post
exports.createPost = (postData) => {
  const newPost = {
    id: posts.length + 1,
    title: postData.title,
    content: postData.content
  };
  posts.push(newPost);
  return newPost;
};

// Update a post
exports.updatePost = (postId, postData) => {
  const postIndex = posts.findIndex(post => post.id === postId);
  if (postIndex !== -1) {
    posts[postIndex] = { id: postId, title: postData.title, content: postData.content };
    return posts[postIndex];
  }
  return null;
};

// Delete a post
exports.deletePost = (postId) => {
  const postIndex = posts.findIndex(post => post.id === postId);
  if (postIndex !== -1) {
    posts.splice(postIndex, 1);
    return true;
  }
  return false;
};

```

## Writing Tests with Supertest, Mocha, and Chai

Install the required dependencies:

```bash
npm install --save-dev mocha chai@4.4.1 supertest
```

Add a test script to the package.json file:

```json
{
  "scripts": {
    "test": "mocha  --exit"
  }
}
```

### Creating the Test File

Create a  `test` directory and a `posts.test.js` file inside it.

```bash
mkdir test
touch test/posts.test.js
```

### Writing Tests

#### `test/posts.test.js`

```javascript
const request = require('supertest');
const chai = require('chai');
const app = require('../app'); // Import the Express application
const expect = chai.expect;

describe('Blog API', function() {
  describe('GET /posts', function() {
    it('should return all posts', async function() {
      const response = await request(app).get('/posts');
      expect(response.status).to.equal(200);
      expect(response.body).to.be.an('array');
      expect(response.body.length).to.be.greaterThan(0);
    });
  });

  describe('POST /posts', function() {
    it('should create a new post', async function() {
      const newPost = { title: 'New Post', content: 'This is a new post' };
      const response = await request(app).post('/posts').send(newPost);
      expect(response.status).to.equal(201);
      expect(response.body).to.include.keys('id', 'title', 'content');
      expect(response.body.title).to.equal(newPost.title);
    });
  });

  describe('PUT /posts/:id', function() {
    it('should update an existing post', async function() {
      const updatedPost = { title: 'Updated Post', content: 'This is an updated post' };
      const response = await request(app).put('/posts/1').send(updatedPost);
      expect(response.status).to.equal(200);
      expect(response.body).to.include.keys('id', 'title', 'content');
      expect(response.body.title).to.equal(updatedPost.title);
    });
  });

  describe('DELETE /posts/:id', function() {
    it('should delete an existing post', async function() {
      const response = await request(app).delete('/posts/1');
      expect(response.status).to.equal(204);
    });
  });
});

```

### Running Tests

Run the tests using Mocha:

```bash
npm test
```

## Checking Test Coverage

Kontrollime, kui palju koodi on kaetud testidega, kasutades `nyc` tööriista.

### `nyc` Install

Install `nyc` to measure code coverage:

```bash
npm install --save-dev nyc
```

### `nyc` configuration 

Add nyc configuration to the  `package.json` file:

```json
{
  "scripts": {
    "test": "nyc mocha --exit"
  },
  "nyc": {
    "reporter": [
      "text",
      "html"
    ],
    "exclude": [
      "test/**"


    ]
  }
}
```

Run tests with `nyc` to view coverage:
```bash
npm test
```

View the HTML report in the `coverage` directory for detailed coverage information.

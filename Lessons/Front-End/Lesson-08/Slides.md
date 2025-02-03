# Web Development

## Front-End Development

Martti Raavel

<martti.raavel@tlu.ee>

---

## Topics for Today

- Review of the previous lecture
- [React and Axios](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Axios/README.md)
- [useEffect Hook](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-UseEffect/README.md)
- [Dynamic Routes](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Routing/README.md#dünaamilised-marsruudid)
- [Conditional Rendering](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Conditional-Rendering/README.md)
- [Flash Messages](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Flash-Messages/README.md)

---

## What Did We Discuss in the Previous Lecture?

---

## React and Axios

We have previously used Axios to make server requests. Axios is a simple and flexible HTTP client that works in both the browser and Node.js. Now that we know how to create a React application with different pages and how to gather data from the user, we can move forward with integrating our application with an API—for logging in, fetching data, etc.

---

## Installing Axios

First, we need to add Axios to our project. We use npm for this:

```bash
npm install axios
```

---

## Using Axios

To use Axios, import it into the desired component. For example:

```javascript
import axios from 'axios';
```

Now we can make requests, such as:

```javascript
const response = await axios.post('https://blog.hk.tlu.ee/login', {
  email: 'user@user.ee',
  password: 'password'
  });
```

---

## Handling the Retrieved Data

After making a request, we receive a response, which we can use. For example, after logging in, we’ll likely receive a token that we’ll need to use in future requests.

```javascript
const token = response.data.token;
```

We can store the token in the user's session or local storage.

```javascript
localStorage.setItem('token', token);
```

---

## Using the Token

With the token stored, we can include it in future requests so the server knows we are logged in.

```javascript
const token = localStorage.getItem('token');

const response = await axios.get('https://blog.hk.tlu.ee/posts', {
  headers: {
    Authorization: `Bearer ${token}`
  }
});
```

---

## useEffect Hook

Let’s say we’re logged into the app and want to view a list of posts. How can we automatically load posts when navigating to the posts page?

We can use the useEffect hook for this.


---

## What is the useEffect Hook?

The useEffect hook is a React hook that allows us to perform actions during the lifecycle of a component. For instance, we can use it to make a server request when a component loads.

```javascript
useEffect(() => {
  const fetchPosts = async () => {
    const response = await axios.get('https://blog.hk.tlu.ee/posts');
    setPosts(response.data);
  };

  fetchPosts();
}, []);
```

---

## How to Use the useEffect Hook

The useEffect hook takes two arguments: a function and an array. The function is what we want to do, and the array indicates when to do it.

If the array is empty, the function runs only once when the component loads. If the array includes a variable, the function runs every time that variable changes.

---
Dynamic Routes

Suppose we have a page displaying a list of posts, with each post having a button to view the post’s content and associated comments on a separate page. It would be impractical to create a separate page for each post.

---

## How to Implement Dynamic Routes

Instead, we can create a single page for posts that uses a dynamic route with the post’s `id`. For example:

```javascript
<Route path="/posts/:id" component={Post} />
```

> `:id`  is a dynamic part of the route that allows us to use it as a variable.
> For example, if we go to `/posts/1`, the `id` will be `1`.

---

## How to Use Dynamic Routes

In a component, we can read dynamic route parameters using the `useParams` hook. For example:

```javascript
const { id } = useParams();
const [post, setPost] = useState(null);

useEffect(() => {
  const fetchPost = async () => {
    const response = await axios.get(`https://blog.hk.tlu.ee/posts/${id}`);
    setPost(response.data);
  };

  fetchPost();
}, [id]);

return (
  <div>
    <h1>{post.title}</h1>
    <p>{post.body}</p>
  </div>
);

```

---

## Conditional Rendering

Conditional rendering is essential in any application. For instance, if we want to display a welcome message to a logged-in user or prompt them to log in if they aren’t.

---

## How to Use Conditional Rendering

There are several ways to implement conditional rendering, such as

- Using an `if` statement
- Using a logical `&&` operator
- Using a ternary operator

---

## Example: `if` Statement

```javascript
import React from 'react';

function UserGreeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign up.</h1>;
}

export default UserGreeting;
```

---

## Example: Logical `&&` Operator

```javascript
import React from 'react';

function Mailbox({ unreadMessages }) {
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&
        <h2>You have {unreadMessages.length} unread messages.</h2>
      }
    </div>
  );
}

export default Mailbox;
```

---

## Example: Ternary Operator

```javascript

import React from 'react';

function Greeting({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? (
        <h1>Welcome back!</h1>
      ) : (
        <h1>Please sign up.</h1>
      )}
    </div>
  );
}

export default Greeting;
```

---

## Flash Messages

Flash messages are temporary notifications displayed to users and then disappear. For example, after a successful login, we might show a message confirming the login, which then fades out.
---

## How to Implement Flash Messages

We can create flash messages using React’s `useState` hook and the`setTimeout` function. For example:

```javascript

const [message, setMessage] = useState(null);

const handleLogin = async () => {
  const response = await axios.post('https://blog.hk.tlu.ee/login', {
    email, password
  });

  if (response.data.token) {
    localStorage.setItem('token', response.data.token);
    setMessage('You have successfully logged in!');
    setTimeout(() => {
      setMessage(null);
    }, 5000);
  } else {
    setMessage('Login failed!');
  }
};

return (
  <div>
    {message && <div>{message}</div>}
    <button onClick={handleLogin}>Login</button>
  </div>
);
  
```

---

## Homework

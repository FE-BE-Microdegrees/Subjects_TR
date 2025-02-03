# React Routing

Routing is an essential part of web applications that allows navigation between different views and components. In React, the `react-router-dom` library is commonly used to manage routes and create a seamless user experience. This chapter covers the basics of React routing, including defining routes, creating links, dynamic routes, and handling 404 pages.

![React-Router](React-Router.webp)

Image Source: Dall-E by OpenAI

- [React Routing](#react-routing)
  - [Learning Outcomes](#learning-outcomes)
  - [Routing in React](#routing-in-react)
    - [What is Routing?](#what-is-routing)
    - [Installing `react-router-dom`](#installing-react-router-dom)
    - [Core Components](#core-components)
  - [Defining Routes](#defining-routes)
    - [Example: Simple Routing](#example-simple-routing)
      - [App.js](#appjs)
      - [Home.js](#homejs)
      - [About.js](#aboutjs)
    - [Creating Links](#creating-links)
      - [Example: Using Links](#example-using-links)
  - [Dynamic Routes](#dynamic-routes)
    - [Example: Dynamic Route](#example-dynamic-route)
      - [User.js](#userjs)
      - [App.js](#appjs-1)
  - [Programmatic Navigation](#programmatic-navigation)
    - [404 Page Handling](#404-page-handling)
      - [Example: Handling a 404 Page](#example-handling-a-404-page)
      - [NotFound.js](#notfoundjs)
      - [App.js](#appjs-2)
  - [Best Practices for Routing](#best-practices-for-routing)
  - [Practical Example: Complete Routing](#practical-example-complete-routing)
    - [App.js](#appjs-3)
    - [Navigation.js](#navigationjs)
    - [Home.js](#homejs-1)
    - [About.js](#aboutjs-1)
    - [User.js](#userjs-1)
    - [NotFound.js](#notfoundjs-1)
  - [Resources](#resources)
  - [Review Questions or Exercises](#review-questions-or-exercises)
  - [Exercises](#exercises)

## Learning Outcomes

By the end of this chapter, learners should be able to:

- Explain what routing is and why it is used in React;
- Install and configure the `react-router-dom` library;
- Create and manage routes in React applications;
- Use links and navigation to move between components;
- Create dynamic routes and handle 404 pages.

## Routing in React

### What is Routing?

Routing enables web applications to provide different views or pages corresponding to user-entered URLs. It allows navigation between pages without reloading the entire page, ensuring a smoother and better user experience.

### Installing `react-router-dom`

To manage routing in React, the `react-router-dom` library is commonly used. Install it using the following command:

```bash
npm install react-router-dom
```

### Core Components

- **BrowserRouter:** The primary container that manages URL history and provides context for routes.
- **Routes:** A component that contains multiple routes.
- **Route:** A component used to define routes and render corresponding components.
- **Link:** Used to create links for navigation without reloading the page.

## Defining Routes

### Example: Simple Routing

#### App.js

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './Home';
import About from './About';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
}

export default App;
```

#### Home.js

```javascript
import React from 'react';

function Home() {
  return <h1>Home Page</h1>;
}

export default Home;
```

#### About.js

```javascript
import React from 'react';

function About() {
  return <h1>About Page</h1>;
}

export default About;
```

### Creating Links

Links enable users to navigate between pages without reloading the entire page.

#### Example: Using Links

```javascript
import React from 'react';
import { Link } from 'react-router-dom';

function Navigation() {
  return (
    <nav>
      <ul>
        <li><Link to="/">Home</Link></li>
        <li><Link to="/about">About</Link></li>
      </ul>
    </nav>
  );
}

export default Navigation;
```

Include the  `Navigation` component in the `App` component to display links on all pages:

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './Home';
import About from './About';
import Navigation from './Navigation';

function App() {
  return (
    <Router>
      <Navigation />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
}

export default App;
```

## Dynamic Routes

Dynamic routes allow displaying different components depending on URL parameters. For instance, dynamic routes can be used to display user profiles where each profile corresponds to a unique ID..

### NExample: Dynamic Route

#### User.js

```javascript
import React from 'react';
import { useParams } from 'react-router-dom';

function User() {
  const { userId } = useParams();
  return <h1>User ID: {userId}</h1>;
}

export default User;
```

#### App.js

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './Home';
import About from './About';
import User from './User';
import Navigation from './Navigation';

function App() {
  return (
    <Router>
      <Navigation />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/user/:userId" element={<User />} />
      </Routes>
    </Router>
  );
}

export default App;
```

## Programmatic Navigation

Programmatic navigation allows the application to navigate between pages using the `useNavigate` hook. For instance, redirecting users to another page after logging in:


```javascript
import { useNavigate } from 'react-router-dom';

function Login() {
  const navigate = useNavigate();

  function handleLogin() {
    // Sisselogimise loogika
    navigate('/dashboard');
  }

  return (
    <button onClick={handleLogin}>Login</button>
  );
}
```

### 404 Page Handling

404 pages display friendly error messages when users navigate to non-existent pages.

#### Example: Handling a 404 Page

#### NotFound.js

```javascript
import React from 'react';

function NotFound() {
  return <h1>404 - Page Not Found</h1>;
}

export default NotFound;
```

#### App.js

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './Home';
import About from './About';
import User from './User';
import NotFound from './NotFound';
import Navigation from './Navigation';

function App() {
  return (
    <Router>
      <Navigation />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/user/:userId" element={<User />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </Router>
  );
}

export default App;
```

## Best Practices for Routing

- **Clear and descriptive URLs:**  Use clear and descriptive URLs reflecting the page content.
- **Navigation components:** Use navigation components like `Link` to enable smooth navigation.
- **404 page handling:** Add a 404 page to handle non-existent routes.
- **Dynamic routes:** Use dynamic routes to display components based on URL parameters.

## Practical Example: Complete Routing

### App.js

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './Home';
import About from './About';
import User from './User';
import NotFound from './NotFound';
import Navigation from './Navigation';

function App() {
  return (
    <Router>
      <Navigation />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/user/:userId" element={<User />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </Router>
  );
}

export default App;
```

### Navigation.js

```javascript
import React from 'react';
import { Link } from 'react-router-dom';

function Navigation() {
  return (
    <nav>
      <ul>
        <li><Link to="/">Home</Link></li>
        <li><Link to="/about">About</Link></li>
        <li><Link to="/user/1">User 1</Link></li>
        <li><Link to="/user/2">User 2</Link></li>
      </ul>
    </nav>
  );
}

export default Navigation;
```

### Home.js

```javascript
import React from 'react';

function Home() {
  return <h1>Home Page</h1>;
}

export default Home;
```

### About.js

```javascript
import React from 'react';

function About() {
  return <h1>About Page</h1>;
}

export default About;
```

### User.js

```javascript
import React from 'react';
import { useParams } from 'react-router-dom';

function User() {
  const { userId } = useParams();
  return <h1>User ID: {userId}</h1>;
}

export default User;
```

### NotFound.js

```javascript
import React from 'react';

function NotFound() {
  return <h1>404 - Page Not Found

</h1>;
}

export default NotFound;
```

## Sources

- [React Router Documentation](https://reactrouter.com/)
- [React Official Documentation - Main Concepts](https://reactjs.org/docs/getting-started.html)
- [JavaScript Front-End Frameworks and Libraries](https://www.javascriptstuff.com/)

## Review Questions or Exercises

- What is routing, and why is it important in React?
- How do you install and configure the react-router-dom library?
- How do you create simple and dynamic routes in React?
- How do you use the Link component to enable navigation?
- How can you handle 404 pages in a React application?

## Exercises

- Create a new React project using Create React App.
- Install the react-router-dom library.
- Build a multi-page application with Home, About, and Contact pages using routing.
- Add navigation components to allow switching between pages.
- Create a dynamic route to display user profiles where each profile corresponds to a unique ID.
- Add a 404 page to handle non-existent routes.


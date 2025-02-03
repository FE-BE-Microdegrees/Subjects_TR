---
marp: true

---
# Web Development

## Front-End Development



---

## Today's Topics

- Review of the previous lecture
- [React Router](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Routing/README.md)
- Not Found Page
- [React Forms](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Forms/README.md)

---

## What did we discuss in the last lecture?

---

## React Router / Routing

Routing allows web applications to display different views or pages based on the URL entered by the user. Routing enables navigation between pages without reloading the entire page, providing a smoother and better user experience.

---

## React Router Components

- **BrowserRouter:** The main container that manages URL history and provides context for routing.
- **Routes:** A component that contains different routes.
- **Route:** A component used to define a route and render the corresponding component.
- **Link:** Used to create links that enable navigation without reloading the page.

---

## Installing React Router

```bash
npm install react-router-dom
```

---

## Using React Router

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

---

## Navigation

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

---

## Programmatic Navigation

Sometimes it’s necessary to navigate programmatically, such as after login, when the user is redirected to another page.

```javascript
import { useNavigate } from 'react-router-dom';

function Login() {
  const navigate = useNavigate();

  function handleLogin() {
    // Login logic
    navigate('/dashboard');
  }

  return (
    <button onClick={handleLogin}>Login</button>
  );
}
```

---

## Not Found Page

When a user enters a URL that doesn’t match any route, a Not Found page is displayed.

```javascript
<Router>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
    <Route path="/login" element={<Login />} />
    <Route path="*" element={<NotFound />} />
  </Routes>
</Router>
```

---

## React Forms

Forms are an essential part of web applications as they allow users to input and submit data. React enables the creation of forms that are dynamic and responsive to user input.

---

## Types of React Forms

- Controlled Components
- Uncontrolled Components

---

## Controlled Components

In controlled components, the component’s state controls the form elements' values. All data in the inputs is stored in the component’s state and updated via event handlers.

---

## Controlled Components - Example

```javascript
import React, { useState } from 'react';

function ControlledForm() {
  const [name, setName] = useState('');

  function handleChange(event) {
    setName(event.target.value);
  }

  function handleSubmit(event) {
    event.preventDefault();
    alert(`Hello, ${name}!`);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" value={name} onChange={handleChange} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## Uncontrolled Components

In uncontrolled components, form element values are not tied to the component’s state. Form values can be read from the DOM using `ref`s to access form values.

> `useRef` is a React hook that creates a reference variable for accessing DOM elements or components.

---

## Uncontrolled Components - Example

```javascript
import React, { useRef } from 'react';

function UncontrolledForm() {
  const nameRef = useRef();

  function handleSubmit(event) {
    event.preventDefault();
    alert(`Hello, ${nameRef.current.value}!`);
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={nameRef} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## What if there are many fields in the form?

When a form has many fields, it’s wise to use an object to manage form data.

```javascript
import React, { useState } from 'react';

function ComplexForm() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    password: '',
  });

  function handleChange(event) {
    const { name, value } = event.target;
    setFormData({ ...formData, [name]: value });
  }

  function handleSubmit(event) {
    event.preventDefault();
    alert(`Hello, ${formData.name}!`);
  }
...

```

---

```javascript
...
  return (
    <form onSubmit={handleSubmit}>
      <input type="text" name="name" value={formData.name} onChange={handleChange} />
      <input type="email" name="email" value={formData.email} onChange={handleChange} />
      <input type="password" name="password" value={formData.password} onChange={handleChange} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## Homework

- Implement React Router in your web application.
- Add a Not Found page.
- Add a login form to your application and read the user input from the form.

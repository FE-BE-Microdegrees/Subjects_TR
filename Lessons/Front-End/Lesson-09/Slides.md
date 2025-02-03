---
marp: true

---
# Web Development

## Front-End Development



---

## Today's Topics

- Review of the previous lecture
- [Token Decoding](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Decode-JWT/README.md)
- [Context API](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Context-API/README.md)
- Managing Login Data with Context
- User List Component and Display

---

## What Did We Discuss Last Time?

---

## JWT

As we saw in the last lecture, we often use JWT (JSON Web Token) for user authentication.

- JWT is an encoded string containing user information.
- It consists of three parts: header, payload, and signature.

---

## Decoding JWT in React

We use the `jwt-decode` library to decode JWT in React.

```bash
npm install jwt-decode
```

Usage

```javascript
import { jwtDecode } from 'jwt-decode';

const decoded = jwtDecode(token);

console.log(decoded);
```

---

## Context API

The Context API is a solution provided by React that allows data sharing between components. It’s an alternative to passing `props`and helps avoid the "prop drilling" problem, where data needs to be passed through multiple components.


---

## Context API Components

Context API consists of the following components:

- `React.createContext()` - creates a context object
- `Provider` - component that provides data
- `Consumer` - component that consumes the context data
- `useContext` - hook for accessing context data

---

## Using Context API

Let's create a separate file to manage authentication-related data.

```javascript
// AuthContext.js
import { createContext } from 'react';

// Create and export the context object
export const AuthContext = createContext();

```

---

## Using Context API

Add a `Provider` component in the same file to provide shared data.

```javascript
// AuthContext.js
import { createContext, useState } from 'react';

export const AuthContext = createContext();

const AuthProvider = ({ children }) => {
  const [user, setUser] = useState(null);

  return (
    <AuthContext.Provider value={{ user, setUser }}>
      {children}
    </AuthContext.Provider>
  );
};

export default AuthProvider;
```

---

## Using Context API

Now, add the `AuthProvider` component inside the `App` component to wrap all components that need authentication data.

```javascript
// App.js

import { AuthProvider } from './AuthContext';

const App = () => (
  <AuthProvider>
    <Main />
  </AuthProvider>
);
```

---

## Using Context API

Now we can use the `useContext` hook to access the context data.

```javascript
// Login.js

import { useContext } from 'react';
import { AuthContext } from './AuthContext';

const Login = () => {
  // Destructure context data - note it's an object, not an array
  const { user, setUser } = useContext(AuthContext);

  return (
    <div>
      {
        user ? (
          <p>Hello, {user.name}</p>
        ) : (
          <button onClick={() => setUser({ name: 'User' })}>Login</button>
        )
      }
    </div>
  );
};

export default Login;

```

---

## Using Context API

We can also add functions to the context that modify the context data.

```javascript
// AuthContext.js

export const AuthProvider = ({ children }) => {
  const [user, setUser] = useState(null);

  const login = () => {
    setUser({ name: 'User' });
  };

  const logout = () => {
    setUser(null);
  };

  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
};
```

---

## Using Context API

Now we can use the `login` and `logout` functions in the `Login` component.

```javascript
// Login.js

import { useContext } from 'react';

import { AuthContext } from './AuthContext';

const Login = () => {
  const { user, login, logout } = useContext(AuthContext);

  return (
    <div>
      {
        user ? (
          <button onClick={logout}>Logi välja</button>
        ) : (
          <button onClick={login}>Logi sisse</button>
        )
      }
    </div>
  );
};

export default Login;
```

---

## Displaying the User List Component

Now we can rewrite our application's navigation menu so that the user list component only appears if the user is logged in and is an administrator.

```javascript
import { AuthContext } from './AuthContext';

function NavBar() {
  const { user } = useContext(AuthContext);
  
  return (
...
    <Nav.Link as={Link} to='/posts'>Posts</Nav.Link>
    {user?.role === 'admin' && <Nav.Link as={Link} to='/users'>Users</Nav.Link>}
    <Nav.Link as={Link} to='/about'>About</Nav.Link>
  </Nav>
...
  );
};
```

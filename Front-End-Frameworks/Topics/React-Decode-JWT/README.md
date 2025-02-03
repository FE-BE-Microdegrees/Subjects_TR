# JSON Web Token (JWT) Decoding in React

JSON Web Token (JWT) is a compact and URL-friendly standard used for secure and compact information exchange. JWT consists of three parts: the header, payload, and signature. The payload typically stores user information and related metadata, which can be utilized in your application.

When a React application uses an API that returns a JWT as an authentication token, you can decode it to extract useful information like user roles, permissions, and other related data.

## JWT Decoding in React

To decode JWT and read its payload in React, you can:

- **Use libraries**: Libraries like `jwt-decode` simplify the decoding process.
- **Decode manually**: Use JavaScript's built-in functions to decode JWTs.

---

### Example: Decoding JWT with `jwt-decode`

The `jwt-decode` library allows you to decode JWTs quickly and easily without processing them manually.

#### Installing `jwt-decode`

Install the `jwt-decode` library in your project:

```bash
npm install jwt-decode
```

#### Decoding JWT and Reading Its Information

Use `jwt-decode`to decode a JWT and extract its payload.

```javascript
// JWTDecoder.js
import React from 'react';
import { jwtDecode } from 'jwt-decode';

const JWTDecoder = ({ token }) => {
  if (!token) {
    return <p>No token provided</p>;
  }

  try {
    // Dekodeeri JWT kasulik koormus
    const decoded = jwtDecode(token);
    return (
      <div>
        <h3>Decoded JWT Payload:</h3>
        <pre>{JSON.stringify(decoded, null, 2)}</pre>
      </div>
    );
  } catch (error) {
    return <p>Invalid token</p>;
  }
};

export default JWTDecoder;
```

### Example: Decoding JWT Manually

If you prefer to decode a JWT without using external libraries, you can decode its Base64-encoded payload manually.

#### Manual Decoding

```javascript
// ManualJWTDecoder.js
import React from 'react';

const base64UrlDecode = (str) => {
  // Asenda - ja _ märgid vastavalt Base64 standardile
  const base64 = str.replace(/-/g, '+').replace(/_/g, '/');
  return decodeURIComponent(
    atob(base64)
      .split('')
      .map((c) => '%' + ('00' + c.charCodeAt(0).toString(16)).slice(-2))
      .join('')
  );
};

const decodeJWT = (token) => {
  const [, payload] = token.split('.');
  return JSON.parse(base64UrlDecode(payload));
};

const ManualJWTDecoder = ({ token }) => {
  if (!token) {
    return <p>No token provided</p>;
  }

  try {
    // Dekodeeri JWT kasulik koormus käsitsi
    const decoded = decodeJWT(token);
    return (
      <div>
        <h3>Decoded JWT Payload:</h3>
        <pre>{JSON.stringify(decoded, null, 2)}</pre>
      </div>
    );
  } catch (error) {
    return <p>Invalid token</p>;
  }
};

export default ManualJWTDecoder;
```

## Example: Using JWT in a React Application

Combine JWT decoding with React Context API to store user authentication data in application state and extract information from the JWT.

### Setting Up Context for Authentication

```javascript
// AuthContext.js
import React, { createContext, useState, useEffect } from 'react';
import { jwtDecode } from 'jwt-decode';

export const AuthContext = createContext();

export const AuthProvider = ({ children }) => {
  const [user, setUser] = useState(null);

  useEffect(() => {
    // Võta localStorage'ist token
    const token = localStorage.getItem('token');
    if (token) {
      try {
        const decodedUser = jwtDecode(token);
        setUser(decodedUser);
      } catch (error) {
        console.error('Invalid token');
        setUser(null);
      }
    }
  }, []);

  const login = (token) => {
    localStorage.setItem('token', token);
    const decodedUser = jwtDecode(token);
    setUser(decodedUser);
  };

  const logout = () => {
    localStorage.removeItem('token');
    setUser(null);
  };

  return (
    <AuthContext.Provider value={{ user, login, logout }}>
      {children}
    </AuthContext.Provider>
  );
};
```

### Displaying User Information

Use `AuthContext` to display user information when they are logged in.

```javascript
// UserProfile.js
import React, { useContext } from 'react';
import { AuthContext } from './AuthContext';

const UserProfile = () => {
  const { user, logout } = useContext(AuthContext);

  if (!user) {
    return <p>No user logged in</p>;
  }

  return (
    <div>
      <h3>User Profile</h3>
      <pre>{JSON.stringify(user, null, 2)}</pre>
      <button onClick={logout}>Logout</button>
    </div>
  );
};

export default UserProfile;
```

### Review Questions

1. How can you decode JWT in React to extract information?
2. What are the differences between using  `jwt-decode` and manual decoding?
3. How can you integrate JWT decoding with React Context API?

### Exercise

- **Create an application that reads and displays user information from a JWT**: Use `jwt-decode` or manually decode the JWT to build an application that displays user information from the token.
- **Integrate JWT decoding into an authentication context**:  Extend the previous example to store user authentication data and roles in React Context API.
### References

- [JWT Documentation](https://jwt.io/introduction/)
- [jwt-decode - NPM](https://www.npmjs.com/package/jwt-decode)
- [React Documentation - Context](https://reactjs.org/docs/context.html)

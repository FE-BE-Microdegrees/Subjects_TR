---
marp: true

---
# Web Development

## Front-End Development

---

## Today's Topics

- Review of the previous lecture
- [Authentication and Authorization](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Back-End-Frameworks/Topics/Auth/README.md)
- [Browser Storage Technologies](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/Browser-Memory/README.md)
- [JWT](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Back-End-Frameworks/Topics/JWT/README.md)
- Sending Headers with Axios Requests
- Implementing Authentication and Authorization

---

## Review of the Previous Lecture

---

## Authentication and Authorization

Authentication is a process by which a user, system, or other entity verifies the claimed identity of another entity, usually based on some form of identity proof:

- Something you know (e.g., password, PIN, CAPTCHA, security question)
- Something you have (e.g., ID card, phone number, email, hardware key)
- Something you are (e.g., fingerprint, facial recognition, iris structure)

---

## Authorization

Authorization is the process that grants (or denies) access rights to network resources. Many e-commerce security systems use a two-step process: authentication to verify identity, followed by authorization to grant access to resources intended for that user.

---

## How Does Authentication and Authorization Work in an API?

- Identifying the user - how?
- User permissions?
- When and how are user permissions verified?

---

## Browser Storage Technologies

- LocalStorage
- SessionStorage
- Cookies
- IndexedDB

---

## LocalStorage

**Local Storage** is persistent storage that allows web applications to store key-value pairs. Data remains even after reloading the page or closing the browser. Local Storage is useful for saving user preferences, session states, and other persistent data.

---

## LocalStorage Example

```javascript
// Storing data
localStorage.setItem('key', 'value');

// Retrieving data
const value = localStorage.getItem('key');

// Removing data
localStorage.removeItem('key');

// Clearing all data
localStorage.clear();
```

---

## SessionStorage

**Session Storage** is temporary storage that holds data only for the duration of the browsing session. Data is deleted after reloading the page or closing the browser.

---

## SessionStorage Example

```javascript
// Storing data
sessionStorage.setItem('key', 'value');

// Retrieving data
const value = sessionStorage.getItem('key');

// Removing data
sessionStorage.removeItem('key');

// Clearing all data
sessionStorage.clear();

```

---

## Cookies

**Cookies** are small blocks of data stored by the browser and sent to the server with each request to the same origin. Cookies are commonly used for user authentication and session management
---

## Using Cookies

```javascript
// Setting a cookie
document.cookie = "username=JohnDoe; expires=Fri, 31 Dec 2021 12:00:00 UTC; path=/";

// Reading cookies
const cookies = document.cookie;
console.log(cookies);

// Removing a cookie (by setting the expiration date to the past)
document.cookie = "username=JohnDoe; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/";

```

---

## IndexedDB

**IndexedDB** is a low-level API that allows storing large amounts of structured data on the user’s device. It's designed for complex database operations and supports indexes and transactions.

---

## JSON Web Token (JWT)

JWT (JSON Web Token) is an open standard (RFC 7519) used to securely transmit information between parties as JSON. It's especially useful for authentication and information exchange, enabling secure and efficient data transfer. JWT is compact and commonly used in web application authentication and authorization.

---

## JWT Components

A JWT consists of three parts, separated by dots (.):

- Header
- Payload
- Signature

---

## Header

Contains information about the token type and the signature algorithm used (e.g., HMAC SHA256 or RSA).

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

---

## Payload

Contains claims, which are the pieces of information encoded in the JWT. Claims can be standardized, public, or private.

```json
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```

---

## Allkiri

The signature is generated using the header and payload, along with a secret key. It verifies the integrity and authenticity of the JWT.

---

## JWT Structure

JWT structure is as follows:
  
```bash
xxxxx.yyyyy.zzzzz
```

where : xxxxx  is the header, yyyyy  is the payload, and zzzzz is the signature, all in base64-url encoding.


---

## JWT Example

```bash
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

---

## Using JWT

How can we use JWT in authentication and authorization processes?

---

## Sending Data to an Express API - Headers

Often, data needs to be sent to an API along with authentication and authorization information. How can we do this?

---

## Authorization Header

The `Authorization` header can carry the necessary authentication information, such as a JWT token.


---

## Sending Headers with Axios

We often need to send headers with requests to APIs. For instance, an authentication token may be required if the API requires authorization. Here’s how to send headers with Axios:

```javascript
async function fetchUser(userId) {
  try {
    const response = await axios.get(`https://jsonplaceholder.typicode.com/users/${userId}`, {
      headers: {
        Authorization: 'Bearer my-auth-token'
      }
    });
    console.log(response.data);
  } catch (error) {
    console.error('Request error:', error);
  }
}

fetchUser(1);

```

---

## Implementing Authentication and Authorization

---

## Homework

- Read through today’s lecture materials
- ...

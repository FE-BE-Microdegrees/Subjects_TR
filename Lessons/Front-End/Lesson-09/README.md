---
marp: true

---
# Web Development

## Front-End Development

Martti Raavel

<martti.raavel@tlu.ee>

---

## Today's Topics

- Review of the previous lecture
- [Token Decoding](../../../Subjects/Front-End-Frameworks/Topics/React-Decode-JWT/README.md)
- [Context API](../../../Subjects/Front-End-Frameworks/Topics/React-Context-API/README.md)
- Managing Login Data with Context
- User List Component and Conditional Rendering

---

## What Did We Discuss Last Time?

---

## JWT Token Decoding

We'll be working with `JWT` (JSON Web Token) again today for authentication. This involves:

- Decoding the token to extract user information.
- Using libraries like `jwt-decode` to handle this decoding in React.

---

## Context API in React

The Context API is a feature in React for sharing data between components, avoiding the need for prop drilling. We'll use it to manage authentication data across our application.

### Key Context Components:

- `createContext()` - Creates a context object.
- `Provider` - Shares data with child components.
- `useContext` - Accesses context data in components.

---

## Using Context API for Login Data

We’ll set up a context to manage login state and user information, making it available throughout the app.

---

## Download and Prepare the Project Code

We’ll use prepared code in this lecture for easier practice and consistency.

1. Download the project code [here](./code/blog.zip).
2. Extract the `.zip` file.
3. Open the folder in a code editor (e.g., VS Code).
4. Run `npm install` in the terminal to install dependencies.
5. Start the app with `npm start`.

For any setup issues, contact the instructor.

---

## Lecture 9 Materials and Links

- [Lecture 8](../Lesson-08/README.md)
- [Code for Lecture 9](./code/blog.zip)
- [Lecture 9 Slides](Slides.md)
- [Code Written During Lecture 9]()
- [Lecture 9 Recording]()
- [Lecture 10](../Lesson-10/README.md)
- [Zoom Link]()

### Topics

- Review of the previous lecture
- [Token Decoding](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Decode-JWT/README.md)
- [Context API](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Context-API/README.md)
- Managing Login Data with Context
- User List Component and Conditional Rendering

### Homework

Review the Lecture 9 materials:

- [Token Decoding](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Decode-JWT/README.md)
- [Context API](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Frameworks/Topics/React-Context-API/README.md)

#### Homework Task

Implement login data management with context in your blog application. When the user is logged in, their name should be visible in all components where needed.

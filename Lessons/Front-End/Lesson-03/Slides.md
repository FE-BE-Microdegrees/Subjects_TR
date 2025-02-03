---
marp: true

---
# Web Development

## Front-End Development

---

## Today's Topics

- Review of the Previous Lecture
- Using Multiple JS Files
- [HTML Forms](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/HTML-Forms/README.md)
- [HTML Forms and JavaScript](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/Forms-and-JS/README.md)

---

## What Did We Cover Last Time?

---

## Using Multiple JavaScript Files in HTML

JavaScript code can be divided into multiple files to keep the code logically separated and easier to manage.

Since JavaScript cannot import other files directly (because JavaScript running in the browser cannot access the filesystem), you must use the HTML `<script>` element.

---

## Multiple JS Files in HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <script src="script1.js"></script>
  <script src="script2.js"></script>
</body>
</html>
```

---

## Order of JS Files

Pay attention to the file order, as JavaScript code is loaded and processed sequentially. This means that if `script2.js` uses a function defined in `script1.js`, `script1.js` must be loaded before script2.js.
---

## HTML Forms

An HTML form consists of one or more input fields that users can fill out.

Forms allow users to submit information, such as names, addresses, and passwords, necessary for tasks like creating an account, logging in, or searching for data.
---

## HTML vormide põhielemendid

- `<form>` - Defines the form and its properties, such as `action` and `method`
- `<input>` - Creates input fields for various types of data
- `<label>` - Allows text labels for input fields
- `<textarea>` - Allows multi-line text input
- `<select>` and `<option>` - Creates dropdown menuss
- `<checkbox>` and `<radio>` - Creates checkboxes and radio buttons
- etc ...

---

## HTML Form Attributes

Various attributes can be added to HTML form elements to specify form behavior, appearance, and other properties.

- `action` - Specifies the URL to send form data to
- `method` - Specifies the method of data submission, usually `GET` or `POST`
- `name` - Specifies the name of the form element
- `type` - Specifies the type of form element
- `required` - Specifies if the form element is mandatory
- etc ...

---

## HTML Form Example: Simple Registration Form

```html
<h1>
  Registration Form
</h1>

<form action="/submit-form" method="POST" id="userInfoForm">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>
  <br>
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>
  <br>
  <label for="password">Password:</label>
  <input type="password" id="password" name="password" required>
  <br>
  <button type="submit">Register</button>
</form>


```

---

## Handling HTML Forms with JavaScript

You can read and process HTML form data using JavaScript.

```javascript

document.getElementById('userInfoForm').addEventListener('submit', (event) => {
  event.preventDefault(); // Stops the default form submission

  const username = document.getElementById('name').value;
  const email = document.getElementById('email').value;
  const password = document.getElementById('password').value;

  const userData = {
    username,
    email,
    password,
  };

  console.log(userData);
  // Proceed to process or send the data to the server
});


```

---

## Validating HTML Forms with JavaScript

Form data can be checked and validated using JavaScript with the `checkValidity()` method.

```javascript
if (email.checkValidity()) {
  // If email is valid
} else {
  // If email is invalid
}
```

---

## Displaying Error Messages in JavaScript Form Validation

You can also show error messages with JavaScript when form data is entered incorrectly.

```javascript
if (!email.checkValidity()) {
  console.log(email.validationMessage);
}
```

---

## Homework

- Use HTML forms for entering blog posts
- Display blog posts from a separate file

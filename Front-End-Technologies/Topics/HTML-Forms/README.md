# HTML Forms: Creation and Handling

This guide explores the creation and handling of HTML forms. Forms are essential components of web pages, enabling users to input data and interact with websites.

![HTML-Forms](HTML-Forms.webp)

*Image Source: Dall-E by OpenAI*

- [HTML Forms: Creation and Handling](#html-forms-creation-and-handling)
  - [Learning Outcomes](#learning-outcomes)
  - [What is an HTML Form?](#what-is-an-html-form)
  - [Key HTML Form Elements](#key-html-form-elements)
    - [HTML Form Attributes](#html-form-attributes)
  - [HTML Form Example: Simple Registration Form](#html-form-example-simple-registration-form)
  - [Additional HTML Form Elements](#additional-html-form-elements)
    - [Dropdown Menu (Select and Option)](#dropdown-menu-select-and-option)
    - [Checkbox](#checkbox)
    - [Radio Button](#radio-button)
  - [Submitting and Handling Form Data](#submitting-and-handling-form-data)
  - [Conclusion](#conclusion)
  - [References](#references)

## Learning Outcomes

After completing this guide, you will be able to:

- Create HTML forms using various input elements;
- Understand the process of form submission;
- Handle form data securely.

## What is an HTML Form?

An HTML form consists of one or more input fields that users can fill out. Forms enable users to submit information, such as names, addresses, and passwords, for tasks like account creation, login, or data searching.

## Key HTML Form Elements

Forms use the `<form>` element to define how data will be sent to the server. Key form elements include:

- **`<form>`**: Defines the form and its properties, such as `action` (the target URL for form data) and `method` (the data submission method, typically `GET` or `POST`).
- **`<input>`**: Creates input fields for various types of data, such as text, passwords, and numbers.
- **`<label>`**: Defines labels for input fields, improving accessibility and user experience.
- **`<textarea>`**: Allows multi-line text input.
- **`<button>`**: Creates buttons for submission or reset actions.
- **`<select>` and `<option>`**: Create dropdown menus for selection.
- **`<checkbox>` and `<radio>`**: Create checkboxes and radio buttons for selection.

### HTML Form Attributes

Forms can include attributes that define their behavior, appearance, and more. Common attributes include:

- `action`: Specifies the URL to send the form data.
- `method`: Specifies the data submission method (`GET` or `POST`).
- `name`: Defines the form element's name.
- `id`: Specifies the form element's unique identifier.
- `required`: Indicates that the form element is mandatory.
- `placeholder`: Specifies placeholder text in the form element.
- `value`: Sets a default value for the form element.
- `type`: Defines the form element's type, such as `text`, `email`, `password`, `checkbox`, etc.
- `for`: Links a `<label>` element to an `<input>` element.
- `checked`: Indicates whether a checkbox or radio button is selected by default.
- `selected`: Specifies whether an option is selected by default in a dropdown menu.
- `disabled`: Indicates whether a form element is disabled by default.

## HTML Form Example: Simple Registration Form

```html
<h1>Registration Form</h1>
<body>
  <form action="/submit-form" method="POST">
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
</body>
```

> Using `<label>` tags allows adding text to describe the purpose of input fields. The for attribute of <label> matches the id attribute of the input field, improving accessibility and user experience

This example shows a simple registration form with fields for name, email, and password, and a submit button. The form data is sent to the server via the `POST` method to the `/submit-form` URL.

## Additional HTML Form Elements

### Dropdown Menu (Select and Option)

```html
<label for="country">Country:</label>
<select id="country" name="country">
  <option value="usa">USA</option>
  <option value="canada">Canada</option>
  <option value="uk">United Kingdom</option>
</select>
```

### Checkbox

```html
<input type="checkbox" name="subscribe" id="subscribe">
<label for="subscribe">Subscribe to newsletter</label>
```

### Radio Button

```html
<input type="radio" name="gender" value="male" id="gender-male" checked>
<label for="gender-male">Male</label>
<input type="radio" name="gender" value="female" id="gender-female">
<label for="gender-female">Female</label>
```

## Submitting and Handling Form Data

When a user presses the submit button, the form data is collected and sent to the server using the URL specified in the `action` attribute and the method defined in the `method` attribute.

## Conclusion

HTML forms are essential tools in web development, allowing users to input and submit data. Proper implementation and handling of forms enable secure and user-friendly web applications. Effective use of forms requires good design practices and attention to data security.

## References

- Mozilla Developer Network (MDN) - [HTML Forms](https://developer.mozilla.org/en-US/docs/Learn/Forms)
- W3Schools - [HTML Form Elements](https://www.w3schools.com/html/html_form_elements.asp)

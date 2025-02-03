# Handling HTML Forms with JavaScript

In this guide, we explore how to use JavaScript to read and validate data from HTML forms.

![HTML-Form-JS](HTML-Form-JS.webp)

*Image Source: Dall-E by OpenAI*

- [Handling HTML Forms with JavaScript](#handling-html-forms-with-javascript)
  - [Learning Outcomes](#learning-outcomes)
  - [Reading Form Data with JavaScript](#reading-form-data-with-javascript)
  - [Validating HTML Forms with JavaScript](#validating-html-forms-with-javascript)
  - [Conclusion](#conclusion)
  - [References](#references)

## Learning Outcomes

After completing this guide, you will be able to:

- Read data from HTML forms using JavaScript;
- Validate form data using JavaScript and HTML5 validation methods.

## Reading Form Data with JavaScript

HTML form data can be read and processed using JavaScript. Below is an example of listening to the form submission event and reading data from various form elements.

```html
<form id="userInfoForm">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" required>

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>

  <label for="country">Country:</label>
  <select id="country" name="country">
    <option value="us">United States</option>
    <option value="uk">United Kingdom</option>
    <option value="in">India</option>
  </select>

  <label for="subscribe">Subscribe to newsletter:</label>
  <input type="checkbox" id="subscribe" name="subscribe">

  <button type="submit">Submit</button>
</form>
```

```javascript
document.getElementById('userInfoForm').addEventListener('submit', function(event) {
  event.preventDefault(); // Prevents default form submission

  const username = document.getElementById('username').value;
  const email = document.getElementById('email').value;
  const country = document.getElementById('country').value;
  const subscribe = document.getElementById('subscribe').checked;

  const userData = {
    username,
    email,
    country,
    subscribe,
  };

  console.log(userData);
  // Further processing or sending data to the server can follow here
});

```

## Validating HTML Forms with JavaScript

When using JavaScript to read form data, the default browser validation (e.g., required, email) stops working if we use event.preventDefault(). However, we can still leverage HTML5 validation with the checkValidity() method.

You can validate form inputs before reading data by adding the following code

```javascript
if (!email.checkValidity()) {
  console.log('Invalid email address');
}
```

If the form element does not meet HTML5 requirements (e.g., required, email), the `checkValidity()` method returns `false`. This helps ensure form fields are correctly filled before processing.

Additionally, you can display an error message to the user explaining why form submission failed:

```javascript
if (!email.checkValidity()) {
  console.log(email.validationMessage);
}
```

The `validationMessage` property returns a detailed error message about why the form element failed validation.

Using this approach, you can combine HTML5 form validation with JavaScript for robust and user-friendly form handling.

## Conclusion

HTML forms are powerful tools for collecting data on the web. Leveraging JavaScript to read and process form data enhances interactivity and functionality in web applications. By understanding how to work with various form elements and validation techniques, you can build more user-friendly and secure web applications.

## References

- [MDN Web Docs - HTML Forms](https://developer.mozilla.org/en-US/docs/Learn/Forms)

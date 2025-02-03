# Basic Interaction with a JavaScript Program

This chapter covers simple ways to interact with a JavaScript program.

![JS Input Output](JS-Input-Output.webp)

Image Source: Dall-E by OpenAI

- [Basic Interaction with a JavaScript Program](#basic-interaction-with-a-javascript-program)
  - [Learning Outcomes](#learning-outcomes)
  - [Interacting with a JS Program](#interacting-with-a-js-program)
  - [`alert()`](#alert)
  - [`prompt()`](#prompt)
  - [`confirm()`](#confirm)
  - [`console.log()`](#consolelog)

## Learning Outcomes

After completing this chapter, you will be able to:

- Explain how to interact with a JavaScript program using `alert()`, `prompt()`, `confirm()`, and `console.log()`;
- Use these functions to create user interfaces and collect user input.

## Interacting with a JS Program

Interacting with a program involves engaging with software through various activities, such as giving commands, entering data, receiving feedback, or managing communication between programs.

JavaScript primarily operates within the browser to affect the behavior of web pages. While web pages typically involve HTML for structure, we focus on JavaScript's built-in functions that facilitate basic interaction:

- `alert()`
- `prompt()`
- `confirm()`
- `console.log()`

These functions allow you to display messages, collect input, and debug output, providing a simple way to learn JavaScript fundamentals.

## `alert()`

The `alert()` function displays a message in a dialog box with an "OK" button, halting script execution until the user closes the box.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Alert Example</title>
</head>
<body>
  <script>
    alert('Hello World!');
  </script>
</body>
</html>
```

This script displays a dialog box with the message `Hello World!` .

> Note: While `alert()` is simple, it may not provide the best user experience, especially on mobile devices where dialog boxes can be intrusive.
> 
## `prompt();`

The `prompt()` function displays a dialog box that asks for user input. It includes a text field and two buttons: "OK" and "Cancel."

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Prompt Example</title>
</head>
<body>
  <script>
    const name = prompt("Enter your name:", "Default Name");
    console.log(name);
  </script>
</body>
</html>


```

If the user enters a name and clicks "OK," the entered name is assigned to the`name` variable. Clicking "Cancel" sets `name` to `null`.

> Note: Like `alert()` , `prompt()` may not be the best choice for collecting input in modern web applications.
> 
## `confirm();`

The `confirm()` unction displays a dialog box with a message and "OK" and "Cancel" buttons, typically used to confirm an action.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Confirm Example</title>
</head>
<body>
  <script>
    const userResponse = confirm("Do you want to continue?");
    console.log(userResponse); // true if OK, false if Cancel
  </script>
</body>
</html>

```

The confirm() function returns true if the user clicks "OK" and false if "Cancel."

> Note: Modern web designs often replace confirm() with custom modal dialogs.

## `console.log();`

The  `console.log()` function outputs information to the browser's console, making it an essential tool for debugging and testing.


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Console Log Example</title>
</head>
<body>
  <script>
    console.log("Hello World!");
  </script>
</body>
</html>

```

Open the browser's developer tools (F12 in most browsers) to view the console output.


[Source](https://developer.mozilla.org/en-US/docs/Web/API/console/log)

[Source](https://developer.mozilla.org/en-US/docs/Web/API/Window/confirm)

[Source](https://developer.mozilla.org/en-US/docs/Web/API/Window/prompt)

[Source](https://developer.mozilla.org/en-US/docs/Web/API/Window/alert)

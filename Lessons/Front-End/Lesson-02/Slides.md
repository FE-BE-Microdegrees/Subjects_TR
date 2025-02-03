---
marp: true

---
# Web Development

## Front-End Development

---

## Topics Today

- Review of the last lecture
- Element positioning on a webpage
  - [CSS Display](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/CSS-Display/README.md)
  - [CSS Display Flex](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/CSS-Display-Flex/README.md)
  - [CSS Box Model](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/CSS-Box-Model/README.md)
- [Node vs. Browser](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/NodeJS-vs-JS/README.md)
- [JavaScript in the Browser](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Topics/Javascript-in-Browser/README.md)
  - [Simple Input and Output](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Topics/Primitive-Input-Output/README.md)
- [DOM](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/DOM/README.md)
- [JavaScript Events](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/Events/README.md)
- [DOM Manipulation](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/Manipulating-DOM/README.md)

---

## What Did We Discuss Last Time?

---

## Positioning Elements on a Webpage

---

## CSS Display

The CSS `display` property defines how an element is displayed in the document flow. It is a powerful property because it allows control over element layout without modifying the HTML structure.

---

## Block and Inline Elements

Some elements take up the full width of their container and create line breaks before and after them. These are block elements (e.g., `<h1>`, `<p>`, `<div>`). Others only occupy as much space as their content requires and do not create line breaks, known as inline elements (e.g., `<a>`, `<img>`, `<span>`).

---

## Main Display Values - 1

The `display` property has multiple values, with some of the most common being:

- **`block`**: Makes the element a block element, occupying the full width of its parent and starting on a new line.
- **`inline`**: Makes the element inline, meaning elements are positioned next to each other on the same line, taking up only the necessary space.
- **`inline-block`**: Combines `inline` and `block` behavior. Elements appear inline, but you can set width and height like block elements.

---

## Main Display Values - 2

- **`none`**: Hides the element, making it invisible and non-interactive.
- **`flex`**: Turns the element into a flexible container, allowing flexible arrangement of child elements.
- **`grid`**: Turns the element into a grid container, enabling more complex layouts using a grid structure.
- ...

---

## CSS Display Flex

The `display: flex` CSS property allows you to create flexible, responsive layouts for HTML elements. Flexbox arranges items along a row or column and provides control over the placement, order, sizing, and spacing of items.

---

## Flexbox Properties

When using Flexbox, several properties are available to arrange elements. The most commonly used ones are:

- **`flex-direction`**: Sets the main axis direction for the container—row or column.
- **`justify-content`**: Controls how children are aligned along the main axis within the container.
- **`align-items`**: Aligns children along the cross axis within the container.
- **`flex-wrap`**: Specifies whether children should wrap to the next line or stay on one line.
- **`flex`**: Sets how children share space in the container.
- ...

---

## Using Flexbox - HTML

```html
<div class="container">
    <div class="item">Element 1</div>
    <div class="item">Element 2</div>
    <div class="item">Element 3</div>
</div>
```

---

## Using Flexbox - CSS

To use Flexbox, set the  `display` property to `flex` on the container element. Then you can use other properties to control layout.

```css
.container {
    display: flex; /* Turns the element into a flexible container */
}

.item {
    flex: 1; /* Each item takes equal space */
}

```

---

## Flexbox

It’s essential to understand that multiple sections (containers) can be used on the same page and combined as needed—for example, a separate section for a menu, another for displaying page content, etc. With display: flex, you can create adaptable layouts that adjust to content and screen size while maintaining control over positioning and size.
---

## CSS Box Model

The CSS box model is how CSS defines the size and positioning of elements. Every HTML element is a box, consisting of content, padding, margin, and border.
---

## CSS Box Modele

![CSS Box Model](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/CSS-Box-Model/BoxModel.png)

---

## CSS Box Model - Code Example

```css
.box {
    width: 350px;
    height: 150px;
    margin: 10px;
    padding: 25px;
    border: 5px solid black;
}
```

---

## CSS Box Model - Standard/Alternative

In CSS, there are two box models: standard and alternative. The difference lies in how the element’s width and height are calculated.

---

## Node vs. Browser

Node.js is a server-side JavaScript environment that enables JavaScript to run on the server. The browser is a client-side environment that allows JavaScript to run on a webpage.
---

## JavaScript in the Browser

JavaScript in the browser aims to make web pages more interactive and dynamic by responding to user actions (events).

JavaScript in the browser allows you to modify page content, style, and structure in real-time, respond to user actions (such as button clicks, mouse movements, keyboard input), and interact with the web server (such as sending and receiving data).
---

## Adding JavaScript to HTML

JavaScript code can be added to HTML in several ways:

- **Internal Script**: JavaScript code is within the HTML  `<script>` element.
- **External Script**: JavaScript code is in a separate file, loaded with the HTML `<script src="...">` element.

---

## Adding JavaScript to HTML - Inline Script

```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Example</title>
</head>
<body>
    <h1>Hello, world!</h1>
    <script>
        alert('Hello, world!');
    </script>
</body>
</html>
```

---

Adding JavaScript to HTML - Separate File

```js
// script.js
alert('Hello, world!');
```

```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Example</title>
    <script src="script.js"></script>
</head>
<body>
    <h1>Hello, world!</h1>
</body>
</html>

```

---

## Simple Input and Output

Browser-based JavaScript includes some built-in functions for getting user input and displaying output.

- **`alert()`**: Displays a message box with text.
- **`prompt()`**: Displays a message box prompting the user for input.
- **`confirm()`**: Displays a message box asking the user to confirm.
- **`console.log()`**: Displays a message in the console.

> Note: `alert()`, `prompt()` and `confirm()`are modal windows that pause script execution until the user interacts with them.
>
> These functions are useful for testing and prototyping but are not recommended for production applications.


---

## DOM

The DOM (Document Object Model) is a representation of a webpage’s structure and content, allowing JavaScript to modify page content, style, and structure.

Using the DOM, JavaScript can create, delete, modify, and move HTML elements, attributes, and text, enabling dynamic and interactive web pages that respond to user actions.
---

## JavaScript Events

JavaScript events are user actions that trigger JavaScript code. Events can be user actions (e.g., button click, mouse movement, keyboard input) or browser actions (e.g., page load, mouse hover).

JavaScript events allow webpages to respond to user actions by modifying page content, style, and structure.

---

## JavaScript Events - Examples

Some common events include:

- **`click`**: Triggered when a user clicks an element.
- **`mouseover`**: Triggered when a user moves the mouse over an element.
- **`keydown`**: Triggered when a user presses a key.
- **`load`**: Triggered when the page loads.
- **`submit`**: Triggered when a form is submitted.
- ...

---

## DOM Manipulation

DOM manipulation refers to modifying HTML elements, attributes, and text using JavaScript. It enables creating dynamic and interactive web pages that respond to user actions.

You can manipulate the DOM with methods to select elements, create elements, delete elements, modify elements, and add event listeners.

---

## DOM Manipulation - Example

```html
<!DOCTYPE html>
<html>
<head>
    <title>DOM Manipulation</title>
</head>
<body>
    <h1 id="heading">Hello, world!</h1>
    <button id="button">Change Text</button>
    <script>
        const heading = document.getElementById('heading');
        const button = document.getElementById('button');

        button.addEventListener('click', () => {
            heading.textContent = 'Hello, JavaScript!';
        });
    </script>
</body>
</html>

```

---

## Homework

- Review the materials covered in today’s lecture
- Use CSS `display`, `flex` and `box model` properties to style your blog application
- Add JavaScript code to your blog page that allows you to, for example, change the heading content or add elements (the goal is to practice DOM manipulation and adding events)

---

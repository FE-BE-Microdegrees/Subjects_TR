---
marp: true

---
# Web Development

## Front-End Development



---

## Topics

- Review of the previous lecture
- CSS Position
- CSS Frameworks
- Bootstrap
- Fetching Data from External Sources
  - Axios

---

## Review of the previous lecture

---

## CSS Position

The CSS `position` property allows developers to set an element’s positioning method. This property lets you define how an element is positioned relative to its normal flow or other elements.

---

## CSS Position Values

Main values for the CSS `position` property are:

- static
- relative
- absolute
- fixed
- sticky

---

## CSS Position: static

**Static** is the default value for the `position` property, keeping the element in the document’s normal flow. The top, right, bottom, and left properties do not affect static elements.

```css
div.static {
  position: static;
  border: 3px solid #73AD21;
}
```

---

## CSS Position: relative

**Relative** positions the element relative to its normal position. This allows the element to move without affecting other elements.

```css
div.relative {
  position: relative;
  left: 30px;
  border: 3px solid #73AD21;
}
```

---

## CSS Position: absolute

**Absolute** removes the element from the document’s normal flow and positions it relative to the nearest positioned ancestor. If none exists, it positions relative to the HTML body element.

```css
div.absolute {
  position: absolute;
  right: 0;
  border: 3px solid #73AD21;
}
```

---

## CSS Position: fixed

**Fixed** positions the element relative to the viewport, and it stays in place even when scrolling.

```css
div.fixed {
  position: fixed;
  bottom: 0;
  right: 0;
  width: 200px;
  border: 3px solid #73AD21;
}
```

---

## CSS Position: sticky

**sticky**: is a combination of  `relative` and `fixed` positioning. The element behaves as `relative` until a specific point, where it becomes `fixed` Often used for navigation menus.

```css
div.sticky {
  position: sticky;
  top: 0;
  background-color: green;
  border: 3px solid #73AD21;
}
```

---

## CSS Frameworks

CSS frameworks are pre-written collections of CSS code that provide templates for styles, layouts, and components. They are designed to speed up web development, offering consistent style and support for various design solutions.
---

## Popular CSS Frameworks

- **Bootstrap**
- **Foundation**
- **Tailwind CSS**
- **Bulma**
- etc

---

## Advantages of CSS Frameworks

- **Speed**: Pre-built components and classes save time in developing the visual aspect of web pages
- **Consistency**: Frameworks help maintain design consistency across projects or corporate web pages.
- **Responsiveness**: Most frameworks have built-in support for responsive design, ensuring proper display across different devices.
  
---

## Limitations of CSS Frameworks

- **Limited Customization**: Some frameworks can be overly restrictive, giving developers less flexibility to customize.
- **Learning Curve**: Each framework requires learning specific classes and systems, which can seem complex at first.
- **Additional Load**: Using frameworks can increase load times, especially if many built-in functions are used unnecessarily.


---

## Bootstrap

Bootstrap is one of the most widely used frameworks, offering a rich selection of components like buttons, forms, and navigation bars. Bootstrap is known for its flexible grid system, supporting responsive web design.
---

## Installing Bootstrap

Bootstrap can be installed in various ways:

- Bootstrap-i CDN
- Downloading Bootstrap
- Via npm
- ...

---

## Bootstrap-i CDN

```html
<!-- Bootstrap CSS -->
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/5.3.2/css/bootstrap.min.css">

<!-- Optional JavaScript -->
<!-- jQuery, Popper.js, and Bootstrap JS -->
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.1/dist/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/5.3.2/js/bootstrap.min.js"></script>

```

---

## Bootstrap Grid System

Bootstrap’s grid system is a 12-column system that allows developers to create responsive and dynamic layouts. It divides the screen into 12 equal columns, which can be used to arrange elements by size.

Grid columns are usually placed within a `<div class="row">` element, itself inside a `<div class="container">` or `<div class="container-fluid">` .

---

## Grid Classes

To use the grid system, add classes to HTML elements that specify their width within the 12-column grid.

Examples:

- `.col-6`: Element takes up 6 columns (half of the screen).
- `.col-4`: Element takes up 4 columns (a third of the screen).
- `.col-3`: Element takes up 3 columns (a quarter of the screen).
- `.col-12`: Element takes up the entire width.

---

## Grid System Example

```html
<div class="container border">
    <div class="row border">
        <div class="col-6 border">Column 1</div>
        <div class="col-6 border">Column 2</div>
    </div>
    <div class="row">
        <div class="col-4 border">Column 1</div>
        <div class="col-4 border">Column 2</div>
        <div class="col-4 border">Column 3</div>
    </div>
</div>

```

---

## Bootstrap Buttons

- `.btn`: Basic button class.
- `.btn-primary`: Primary button.
- `.btn-secondary`: Secondary button.
- `.btn-success`: Success button.
- `.btn-danger`: Danger button.
- `.btn-warning`: Warning button.
- `.btn-info`: Info button.

---

## Bootstrap Forms

- `.form-group`: Wraps form elements and adds spacing between them.
- `.form-control`: Applies form element styling.
- `.form-check`: Class used for form elements verification.
- `.form-check-input`: Input class for verification.
- `.form-check-label`: Label class for verification.
- `.form-text`: Label class for verification.
- `.form-inline`: Layout class for inline form elements.
- `.form-horizontal`: Layout class for horizontal form elements.
- etc.

---

## Bootstrap Navigation Bar

- `.navbar`: Basic navbar class.
- `.navbar-expand`: Defines navbar expansion rules.
- `.navbar-light`: Light-themed navbar.
- `.navbar-dark`: Dark-themed navbar.
- `.navbar-brand`: Brand or logo in the navbar.
- `.navbar-nav`: Navbar menu class.
- `.nav-item`: Navbar menu item class.
- `.nav-link`: Navbar menu link class.
- etc.

---

## Fetching Data from External Sources

**Andmete pärimine välisest allikast on oluline osa veebiarendusest, kuna see võimaldab veebilehtedel saada dünaamilisi andmeid ja suhelda serveritega. Üks populaarsemaid viise andmete pärimiseks on kasutada** `Axios`-library.

---

## Axios

Axios is a Promise-based HTTP client for JavaScript, used to send and receive data from a web server. It supports both browser and Node.js environments, making it versatile for various development scenarios.

---

## Installing Axios

Like many other libraries, Axios can be installed in multiple ways, but for browser-based JavaScript, the simplest method is to use the Axios CDN

```html
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
```

---

## Using Axios

Using Axios is straightforward. Here is an example of making a GET request and handling the response using async/await:

```javascript
async function fetchPosts() {
  try {
    const response = await axios.get('https://jsonplaceholder.typicode.com/todos');
    console.log(response.data);
  } catch (error) {
    console.error('Request error:', error);
  }
}

fetchPosts();
```

---

## Running JavaScript Functions in HTML

While we’ve been listening to events and running functions in JavaScript, it’s also possible to trigger JavaScript functions directly in HTML.

```html
<button onclick="myFunction()">Run Function</button>
```

```javascript
const myFunction = () => {
  alert('Hello World!');
};
```

---

## Passing the Event Object

As we discussed in the previous lecture, an event object accompanies an event, containing valuable information about the event. Here’s how to pass it from HTML to JavaScript:

```html
<button onclick="myFunction(event)">Run Function</button>
```

```javascript
const myFunction = (event) => {
  console.log(event);
};
```

---

## Homework

- Read through the fourth lecture materials:
  - [CSS Position](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/CSS-Position/README.md)
  - [CSS raamistikud](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/CSS-Frameworks/README.md)
  - [Bootstrap](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/Bootstrap/README.md)
  - [Andmete pärimine välisest allikast Axios-ega](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/Axios/README.md)
- Create a blog page using Bootstrap.
- Add data fetching to the blog using Axios.
  - Use an API such as [JSONPlaceholder](https://jsonplaceholder.typicode.com/)
  - Display blog posts on the page.
  - Try to display comments for the posts as well.

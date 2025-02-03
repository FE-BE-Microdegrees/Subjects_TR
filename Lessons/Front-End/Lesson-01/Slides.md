---
marp: true

---
# Web Development

## Front-End Development


---

## Topics

- What will we do?
- HTML
- CSS

---

## What will we do?

- Front-End development (user interface)
- Not creating the design but implementing the technical solutions needed to realize it
- HTML, CSS, JavaScript
- CSS frameworks (Bootstrap, Material Design)
- Later, React

---

## HTML - 1

HTML stands for Hyper Text Markup Language.

It is a markup language used to define various types of content rather than instructing the computer as a programming language would.

HTML is a standard markup language for creating web pages, describing the structure of a webpage.

---

## HTML - 2

HTML consists of a series of elements that are used to display or act on content in certain ways. Surrounding content with tags can make a word or image a hyperlink to another page, italicize words, change font sizes, and more.

---

## HTML - 3

HTML does not tell the computer what to do but instead defines what something is. For example, “this is a paragraph,” “this is a heading,” “this is a link,” etc. The browser then knows how to display the written content.

---

## HTML Tags - 1

HTML tags are element names surrounded by angle brackets `<>` and used to create HTML elements, which are the building blocks of HTML pages. HTML tags are keywords inside angle brackets:

```html
<tagname></tagname>
```

---

## HTML Tags - 2

HTML tags usually come in pairs like `<p>` and `</p>`. The first tag in the pair is the opening tag, and the second is the closing tag. The closing tag is written like the opening tag but with a slash before the tag name. Some HTML tags do not have closing tags, such a `<br>` (indicating a line break).

---

## HTML Tags - 3

- `<h1>` - first-level heading;
- `<p>` - paragraph;
- `<div>` - used to create a section in an HTML document;
- `<a>` - link, hyperlink;
- `<img>` - image display tag;
- `<table>` - table creation tag;

---

## HTML Tags - 4

- `<form>` - form creation tag;
- `<input>` - form input field creation tag;
- `<button>` - button;
- `<ul>` - unordered list (bullet points);
- `<ol>` - ordered list (numbered);
- `<li>` - list item;
- etc

---

## HTML Elements - 1

An HTML element is defined by an opening tag, some content, and a closing tag:

```html
<tagname>Content goes here...</tagname>
```

> Tags mark the beginning and end of an HTML element. The content is everything between the opening and closing tags, including the tags themselves.
> 
---

## HTML Elements - 2

For example, the following HTML code defines a first-level heading and a paragraph element:

```html
<h1>This is a heading</h1>
<p>This is a paragraph.</p>

```

The `<h1>` tag defines a first-level heading. The `<p>` tag defines a paragraph.

---

## Nested HTML Elements (nested elements)

HTML elements can be nested (elements can contain elements). Most HTML elements can be nested (except for some HTML elements like  `<br>`).

For example, the following HTML code defines a first-level heading and a paragraph element, and the paragraph element contains a link element:

```html
<h1>This is a heading</h1>
<p>This is a paragraph.
  <a href="https://www.google.com/">Google</a>
</p>
```

---

## Nested HTML Elements - 2

```html
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<ol>
  <li>Item 1</li>
  <li>Item 2</li>
</ol>

```

---

## HTML Attributes - 1

HTML Attributes

Attributes are defined as name/value pairs like this:  `name="value"`.

---

## HTML Attributes - 2

The following HTML code defines a first-level heading with an ID attribute:

```html
<h1 id="heading">This is a heading</h1>
```

The `id` attribute assigns a unique ID to the HTML element. The `id` attribute value must be unique within the HTML document. The `id` attribute is used for element identification via links (using a fragment identifier), scripting, or styling (with CSS).
---

## HTML Attributes - 3

Some tags commonly have attributes. For instance, the `<a>` tag is used to create hyperlinks and typically has an `href` attribute that specifies the URL destination of the link.

The `<img>` tag is used to display an image and typically has a `src` attribute to specify the image URL. The `img`  tag usually includes the `alt` attribute, providing alternative text if the image cannot be displayed.

```html
<a href="https://www.google.com/">Google</a>
<img src="https://www.example.com/image.png" alt="Alternate text">
```

---

## HTML Document Structure

An HTML document is a file containing HTML code. It consists of the following parts:

- HTML document declaration;
- HTML root element;
- HTML head;
- HTML body.

---

## HTML Document Declaration

The HTML document declaration defines the document type and version. This declaration is always written at the beginning of an HTML document.

```html
<!DOCTYPE html>
```

---

## HTML Root Element

The root element of an HTML document is the `<html>` element. This element is the root of the HTML document and contains all content, except the document type declaration.

```html
<html>
  ...
</html>
```

---

## HTML Head

The head of an HTML document is the `<head>` element. It includes information about the document, such as the title, scripts, styles, and metadata.


```html
<head>
  <title>Page title</title>
</head>
```

---

## HTML body

The body of an HTML document is the  `<body>` element. It contains the actual content displayed by the web browser.

```html
<body>
  <h1>This is a heading</h1>
  <p>This is a paragraph.</p>
</body>

```

---

## HTML Document Complete

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <h1>This is a heading</h1>
    <p>This is a paragraph.</p>
  </body>
</html>

```

It’s essential to note that all HTML elements are descendants of the root HTML element.

---

## HTML Document Metadata

HTML document metadata provides information about the document. Metadata can be used by browsers (for how content is displayed or to reload the page), search engines (keywords), etc. Metadata is set in the HTML document’s `head`using the `meta` tag and attributes.

```html
<head>
  <title>Page title</title>
  <meta charset="UTF-8">
  <meta name="description" content="Free web tutorials">
  <meta name="keywords" content="HTML, CSS, JavaScript">
  <meta name="author" content="John Doe">
</head>
```

---

## Viewing an HTML Document

You can view an HTML document in a web browser. Save the HTML code in a file with the extension `.html` or `.htm` and open it in a browser.

---

## Exercises

1. Create an HTML document with a title and a paragraph.
2. Add an image between the title and paragraph.
3. Add a link below the image that leads to Google’s homepage.
4. Add a list containing at least 3 items below the paragraph.
5. Add a table below the list with at least 3 rows and 3 columns.

---

## CSS - 1

CSS stands for Cascading Style Sheets. It is a styling language that describes how HTML elements should be displayed.

CSS is used to style HTML elements by adding colors, fonts, layouts, etc. CSS is one of the core web technologies alongside HTML and JavaScript.

---

## CSS - 2

CSS is designed to separate presentation from content, including layout, colors, and fonts. This separation improves accessibility, provides more flexibility and control over presentation, allows multiple web pages to share styling by setting CSS in a separate `.css` file, and reduces complexity and repetition of structured content.

---

## CSS - 3

While HTML defines the structure of a web page, CSS describes how that structure should appear.

For example, if you want to change the text color on your website, you can do this with CSS. CSS can also change font size, font family, background color, border color, border width, border style, and more.

---

## Applying CSS to HTML

There are three ways to apply CSS to HTML:

- Inline CSS;
- Internal CSS;
- External CSS.

---

## Inline CSS

Inline CSS is applied directly within an HTML element’s attribute. It is used when you only want to style a single HTML element. For example:

```html
<p style="color: red;">This is a red paragraph.</p>

```

---

## Internal CSS

Internal CSS is defined in the `<style>` tag inside the `<head>`of the HTML document. It is used when you want to style the entire HTML document. For example:

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <p>This is a red paragraph.</p>
  </body>
</html>

```

---

## External CSS

External CSS is defined in a separate CSS file. It is used when you want to apply CSS to multiple HTML documents. For example:

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" type="text/css" href="style.css">
  </head>
  <body>
    <p>This is a red paragraph.</p>
  </body>
</html>

```

`style.css` file:

```css
p {
  color: red;
}
```

---

## CSS Selectors - 1

To apply a style to an HTML element, you must select it to specify which element you want to style. HTML elements are selected using CSS selectors.

CSS selectors are used to target specific HTML elements on your web page, making CSS more powerful by allowing you to apply styles to individual elements.

---

## CSS Selectors - 2

With selectors, you can target HTML elements by:

- Tag name;
- Class name;
- ID;
- Attribute;
- Pseudo-class;
- etc

---

## CSS Selectors - 3

When writing CSS, you need to define two things:

- Selector
- Declaration block.

Selectors are used to target HTML elements, and the declaration block is used to define the CSS rules applied to selected elements.

---

## CSS Declaration Block

A declaration block is enclosed in curly braces  `{}`. Inside the braces, you can specify one or more CSS rules. Each CSS rule consists of a property and a value. A colon `:` follows the property, and a semicolon `;` follows the value..

```css
selector {
  property: value;
}

```

---

## Tag Selectors

Tag selectors target HTML elements by their tag name. Selectors are case-insensitive, meaning `p` and `P` are the same. For example, if you want to select all `<p>` elements on your web page:

```css
p {
  color: red;
}
```

---

## Class Selectors

To select all elements with the class `class="my-class"`, you can use the following selector:

```css
.my-class {
   /* CSS rules */
}
```

Class selectors begin with a period `.`, followed by the class name. In this example, the class name is `my-class`.

---

## ID Selectors

To select an element with the ID  `id="my-id"`, use the following selector:

```css
#my-id {
  /* CSS rules */
}
```

ID selectors start with a hash `#`, followed by the ID name. Here, the ID name is `my-id`.

---

## CSS Properties

CSS properties are used to style the selected HTML elements. Each CSS property has a name and a value. The property is followed by a colon`:`, and the value is followed by a semicolon `;`. For example, if you want to change the text color on your website:
```css
p {
  color: red;
}
```

In this example, the property is `color`, and the value is `red`. A colon follows the property, and a semicolon follows the value.

---

## CSS Properties - 2

There are many different CSS properties. Some of the most common CSS properties are:

- `color` - sets the text color;
- `font-size` -  sets the text font size;
- `font-family` - sets the text font family;
- `background-color` - sets the element’s background color;
- `border-color` - sets the border color;
- `border-width` - sets the border width;
- `border-style` - sets the border style;
- `border` - sets the border line.

---

## CSS Properties - 3

- `width` - sets the element’s width;
- `height` - sets the element’s height;
- `margin` - sets the element’s margin;
- `padding` - sets the element’s padding;
- `text-align` - sets the horizontal alignment of text;
- `vertical-align` - sets the vertical alignment of text;
- `display` - sets the element’s display behavior;
- `position` - sets the element’s position;
- etc

---

## CSS Values

CSS values are used to set the value of a CSS property. For example, if you want to change the text color on your website:

```css
p {
  color: blue;
  font-size: 40px;
}
```

This CSS rule applies two properties to all paragraphs on the web page: `color` and `font-size`. The value for `color` is `blue`, and the value for `font-size` is `40px`.

---

## CSS väärtused - Multiple Values

Some CSS properties may require or allow multiple values.

```css
p {
  border: 1px solid black;
}
```

In this example, the `border` property has three values:`1px`, `solid` and `black`. The first value (`1px`) sets the border width. The second value (`solid`)  sets the border style. The last value (`black`) sets the border color.

---

## Units

CSS units are used to set the size of elements. There are two types of CSS units:

- `absolute units`
- `relative units`.

---

## Absolute Units - 1

Absolute units are fixed units that are not relative to anything else. For example, to set an element’s width using an absolute unit:

```css
p {
  width: 100px;
}
```

In this example, the element’s width is `100px`. The width is not relative to anything; it is a fixed `100px`.

---

## Absolute Units - 2

Some common absolute units are

- `cm` - centimeters - 1cm = 37.8px;
- `mm` - millimeters - 1mm = 3.78px;
- `Q` - quarter-millimeters - 1Q = 0.95px
- `in` - inches - 1in = 96px;
- `pc` - picas - 1pc = 16px;
- `pt` - points - 1pt = 1.33px;
- `px` - pixels - 1px = 1/96 inch.

Usually, `px` is used as an absolute unit..

---

## Relative Units - 1

Relative units depend on something else (the parent element, root element, etc.). For example, to set an element’s width using a relative unit:

```css
p {
  width: 100%;
}
```

Here, the element’s width is `100%`, relative to the parent element’s width. If the parent element’s width is `100px`, the element’s width is `100px`. If the parent element’s width is `200px`, the element’s width is `200px`, and so on.
---

## Relative Units - 2

Some common relative units are:

- `%` - percentage;
- `em` - the font size of the parent element;
- `rem` - the font size of the root element;
- `vw` - 1% of the viewport width;
- `vh` - 1% of the viewport height;
- `vmin` - 1% of the smaller dimension (width or height) of the viewport;
- `vmax` - 1% of the larger dimension (width or height) of the viewport;
- etc.

---

## Unit-Free Values  - 1

Some values do not require units. For example, to set an element’s transparency:

```css
p {
  opacity: 0.5;
}
```

Here, the opacity of the element is `0.5`. This value is fixed and not relative to anything.

---

## Unit-Free Values - 2

Some common unit-free values are:

- `opacity` - sets the transparency of the element;
- `z-index` - sets the stacking order of the element;
- `order` - sets the order of the element;
- etc.

---

## CSS Colors

Colors are used to set the color of elements. There are many different ways to define colors in CSS. Some common ways are:

- `color name` - e.g., `red`, `green`, `blue` etc;
- `rgb` - e.g., `rgb(255, 0, 0)`, `rgb(0, 255, 0)`, `rgb(0, 0, 255)` etc;
- `hexadecimal` - e.g., `#ff0000`, `#00ff00`, `#0000ff` etc;
- `rgba` - e.g., `rgba(255, 0, 0, 0.5)`, `rgba(0, 255, 0, 0.5)`, `rgba(0, 0, 255, 0.5)` etc;

---

## CSS värvid - Named Colors

CSS has many named colors. Some common color names are:

- `red` - red color;
- `green` - green color;
- `blue` - blue color;
- `yellow` - yellow color;
- `orange` - orange color;
- `purple` - purple color;
- `pink` - pink color;
- `black` - black color;
- `white` - white color;
- etc

---

## Homework

- Read through the topics covered in this lecture.

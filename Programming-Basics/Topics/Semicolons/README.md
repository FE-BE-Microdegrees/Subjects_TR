# Semicolons in JavaScript

![Semicolons](Semicolons.webp)

*Image source: Dall-E by OpenAI*

- [Semicolons in JavaScript](#semicolons-in-javascript)
  - [Learning Outcomes](#learning-outcomes)
  - [Using Semicolons in JavaScript](#using-semicolons-in-javascript)
  - [Special Cases That Require Semicolons](#special-cases-that-require-semicolons)
  - [Where Are Semicolons Not Used?](#where-are-semicolons-not-used)

## Learning Outcomes

After completing this topic, you will be able to:

- Explain how to use semicolons in JavaScript;
- Explain when semicolons are not required;
- Explain when semicolons are necessary.

## Using Semicolons in JavaScript

In JavaScript (including Node.js), semicolons are used to separate statements and terminate lines of code. In practice, many JavaScript programs omit semicolons, as JavaScript automatically inserts semicolons where necessary.

Here’s an example of a code block without semicolons:

```javascript
let x = 5
let y = 10
let z = x + y
console.log(z)
```

Such code is entirely valid in JavaScript and works exactly the same way as code with semicolons. However, it is considered good practice to always include semicolons in your code to make it more readable and maintainable. This also helps to avoid certain errors that may occur when JavaScript automatically inserts semicolons.

```javascript
let x = 5;
let y = 10;
let z = x + y;
console.log(z);
```

## Special Cases That Require Semicolons

As mentioned, semicolons are not strictly required in JavaScript, but they are considered good practice. However, there are specific situations where semicolons are necessary.

One such situation is when you want to declare two different variables on the same line:

```javascript
let x = 5; const y = 10;
```

In this case, semicolons are needed to separate the declarations.

Another example where JavaScript's automatic semicolon insertion ([ASI](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#automatic_semicolon_insertion)) can lead to unexpected behavior is the following:

```javascript
function getCheese() {
  return 
  { 
      cheeseType: "Gouda"
  } 
}
```

In this example, you might expect the function to return an object describing the cheese type. However, JavaScript interprets the function as follows:

```javascript
function getCheese() {
  return; 
  { 
      cheeseType: "Gouda"
  } 
}
```

As a result, the function returns `undefined` instead of the object.

To avoid such issues, the function should be written like this:

```javascript
function getCheese() {
  return { 
      cheeseType: "Gouda"
  } 
}
```

## Where Are Semicolons Not Used?

Semicolons are not placed at the end of the following statements:

- `if (...) {...} else {...}`
- `for (...) {...}`
- `while (...) {...}`

> Note: However, semicolons are used after `do{...};` `while (...);` 
[Source1](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#automatic_semicolon_insertion)

[Source2](https://dev.to/adriennemiller/semicolons-in-javascript-to-use-or-not-to-use-2nli)

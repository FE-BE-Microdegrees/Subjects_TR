# Javascript Best Practices

![alt text](Javascript-Best-Practices.webp)

- [Javascript Best Practices](#javascript-best-practices)
  - [Learning Outcomes](#learning-outcomes)
  - [Introduction](#introduction)
  - [Javascript Code Style](#javascript-code-style)
    - [Use a Linter When Writing Code](#use-a-linter-when-writing-code)
    - [Start Code Blocks on the Same Line as the Curly Brace](#start-code-blocks-on-the-same-line-as-the-curly-brace)
    - [Use camelCase for Variable and Function Names](#use-camelcase-for-variable-and-function-names)
    - [Prefer `const` for Variables](#prefer-const-for-variables)
    - [Import Modules at the Beginning of Files](#import-modules-at-the-beginning-of-files)
    - [Use `===` and `!==` Operators](#use--and--operators)
    - [Use Template Literals for Strings](#use-template-literals-for-strings)
  - [References](#references)

## Learning Outcomes

After completing this section, you will be able to:

- Describe the importance of best practices in Javascript
- Describe the principles of Javascript code style
- Explain best practices for writing Javascript code

## Introduction

Every programming language has its own best practices, which help us write better and more efficient code. Following best practices is also crucial for code readability and maintainability. Javascript is no exception. Best practices can be categorized into different areas, such as:

- Project architecture
- Error handling
- Code style
- Testing
- Security, etc.

In this material, we will focus on Javascript best practices related to code style.

## Javascript Code Style

### Use a Linter When Writing Code

Linters like [ESLint](https://eslint.org/) help you write code that follows Javascript best practices. Linters help identify various code-related issues and suggest how to fix them. ESLint can be configured to meet project requirements and use different style guides like the [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript), [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html), or [StandardJS](https://standardjs.com/).

If using ESLint seems too complex, you can use [Prettier](https://prettier.io/). Prettier is a tool that automatically formats code according to predefined rules. While it’s not as flexible as ESLint, it’s easy to use and works with most Javascript editors.

### Start Code Blocks on the Same Line as the Curly Brace

```javascript
// Do this
function someFunction() {
  // code block
}

// Avoid this
function someFunction()
{
  // code block
}
```

### Use camelCase for Variable and Function Names

When writing Javascript code, use camelCase for variable and function names. In camelCase, names consist of multiple words, where each word starts with a capital letter except the first one.

```javascript
// Do this
let myVariable = 10;
function myFunction() {
  // code block
}

// Avoid this
let my_variable = 10;
function my_function() {
  // code block
}

```

### Prefer `const` for Variables

When a variable’s value does not change, use `const` to define it. A `const` variable cannot be reassigned, which helps prevent accidental modification. If the value needs to change, use let. It's recommended to avoid using `var`.

### Import Modules 

If your project contains modules, always import them at the beginning of the file, not inside a function.

Importing modules at the start makes the code easier to read and understand since you can immediately see the file’s dependencies. Also, Javascript loads modules synchronously, so loading them at the beginning ensures they are ready before the code execution continues. Importing modules inside a function might cause unexpected pauses in the program's execution.

### Use `===` and `!==` Operators

Write your code to avoid using the less strict comparison operators like `==` and `!=`. Instead, use the stricter `===` and `!==` operators, which also check the value types. For example, `1 === '1'` returns `false` because these two values are of different types. This helps prevent unexpected bugs in the code.

### Use Template Literals for Strings

Template literals are string literals in Javascript that allow variables and expressions within the string. Template literals are enclosed with backticks (`) and use `${}` for variable and expression interpolation. They should be preferred over regular string concatenation methods as they make the code more readable and reduce the likelihood of errors.

```javascript
// Do this
const name = 'John';
const greeting = `Hello, ${name}!`;

// Avoid this
const name = 'John';
const greeting = 'Hello, ' + name + '!';

```

## References

- [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)

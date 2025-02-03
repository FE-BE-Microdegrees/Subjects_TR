---
marp: true
---

# Web Development

---

## Software Development

- Recap of the previous lecture
- [Prototyping](https://github.com/FE-BE-Microdegrees/Subjects/blob/Lessons-translation/Software-Development/Topics/Prototyping/README.md)

---

## Recap of the Previous Lecture

---

## Prototyping - Discussion

---

## Prototyping - What?

Prototyping is a technique used in software development to create early working versions of a software product or system.

Prototyping involves creating a simplified but functional version of the final product, which can be used for gathering feedback, testing ideas, and refining requirements before the final version is built.

---

## Prototyping - Benefits

- Better communication and collaboration between team members and stakeholders
- Early identification of potential issues and areas for improvement
- Reduced risk of misunderstandings between developers and stakeholders
- Faster iteration and testing of design concepts and workflows
- Increased user engagement and satisfaction through early feedback and input

---

## Prototyping - Paper Prototyping

![Paper Prototype of a Mobile Game](https://github.com/FE-BE-Microdegrees/Subjects/blob/Lessons-translation/Software-Development/Topics/Prototyping/Paper_prototype.jpg)

---

## Paper Prototyping

Paper prototyping is a **low-cost** and low-fidelity prototyping technique used in software development to quickly and easily create an interactive representation of a product or system.

---

## Paper Prototyping - Benefits

- Low cost
- Quick iteration
- Improved communication
- Higher user involvement

---

## Paper Prototyping - Drawbacks

- Low precision
- Limited functionality
- Limited usability
- Environmental constraints

---

## Prototyping - Digital Tools

Prototyping tools are an important class of software development tools that help developers quickly create and test interactive user interface (UI) designs without needing to write code.

---

## Digital Prototyping Tools - Example

<https://www.figma.com/proto/XGHH08vXQsVMzVlVVYysi2/Metsake---teacher?node-id=1-3>

---

## Digital Prototyping Tools

- [Figma](https://www.figma.com/)
- [Adobe XD](https://www.adobe.com/ee/products/xd.html)
- [Sketch](https://www.sketch.com/)
- [InVision](https://www.invisionapp.com/)
- [Axure RP](https://www.axure.com/)
- Many other digital tools

---

## Digital Prototyping Tools - Advantages

- Fast iteration
- Real-time collaboration
- Interactive prototypes
- Usability testing
- Support for design systems
- Ability to export code for developers
- ...

---

## Digital Prototyping Tools - Drawbacks

- Higher cost compared to paper prototyping
- Learning curve
- More time-consuming than paper prototyping
- ...

---

## Prototyping - Summary

- Prototyping is a crucial part of software development
- Don't be afraid to use paper and pencil
- Digital tools are great but may require more time and resources
- Sometimes, too much is invested in prototyping
- Sometimes, not enough is invested in prototyping
- ...

---

## Programming

- Recap of the previous lecture
- Solving issues during homework
- [JavaScript Best Practices](https://github.com/FE-BE-Microdegrees/Subjects/blob/Lessons-translation/Programming-Basics/Topics/Javascript-Best-Practices/README.md)
- [Debugging](https://github.com/FE-BE-Microdegrees/Subjects/blob/Lessons-translation/Programming-Basics/Topics/Debugging/README.md)
- Exercises

---

## Recap of the Previous Lecture

---

## Issues During Homework

---

## JavaScript Best Practices - Discussion

---

## JavaScript Best Practices

Every programming language has its best practices, which help us write better and more efficient code.

Additionally, following best practices is important for the readability and maintainability of code. JavaScript is no exception to this.

---

## JavaScript Best Practices - Categories

- Project architecture;
- Error handling;
- Code style;
- Testing;
- Security;
- etc.

---

## JavaScript Code Style

---

## JavaScript Code Style - Code Linters

Use a code linter when writing code to help prevent various code-related issues and improve code readability.

- ESLint
- Prettier
- ...

---

## JavaScript Code Style - Curly Braces for Code Blocks

Start curly braces for code blocks on the same line.

```javascript
// Do this
function someFunction() {
  // code block
}

// Avoid

function someFunction()
{
  // code block
}
```

---

## Curly Braces Example - Why?

```javascript
function test() {
  return { /* <--- curly brace on new line */
    javascript: "fantastic"
  };
}

const r = test();
try {
  console.log(r.javascript); // does this work...?
} catch (e) {
  console.log('no - it broke: ' + typeof r);
}
```

---


Source: <https://stackoverflow.com/questions/3641519/why-do-results-vary-based-on-curly-brace-placement>

---

## JavaScript Code Style - Use camelCase for Variable and Function Names
Use camelCase for variable and function names.

```javascript
// Do this
let myVariable = 10;
function myFunction() {
  // code block
}

// Avoid
let my_variable = 10;
function my_function() {
  // code block
}

```

---

## JavaScript Code Style - Use const for Variable

Prefer using `const` for variables, and avoid using `var` altogether.

---

## Importing Modules

If the project contains modules, always import them at the beginning of the code, not inside a function.

By importing modules at the beginning of the code, it becomes easier to read and understand, and it's clear which dependencies the file has.

---

## Use Strict Comparisons

Use `===` and `!==` operators.

---

## Use Template Literals

Use template literals for string composition.

```javascript
// Do this
const name = 'John';
const greeting = `Hello, ${name}!`;

// Avoid
const name = 'John';
const greeting = 'Hello, ' + name + '!';
```

---

## Debugging

Debugging is the process of finding and fixing programming errors. An error is a bug in the program that causes it to behave unexpectedly during execution.

---

## Silumisvahendid

- NodeJS built-in debugger
- Code editor debuggers
- `console.log()` method
---

## Breakpoint

A breakpoint is a spot in the code where we want the debugger to pause execution and allow us to check variable values.

---

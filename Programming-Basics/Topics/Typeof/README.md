# Typeof Operator

![Typeof](typeof.webp)

*Image source: Dall-E by OpenAI*

- [Typeof Operator](#typeof-operator)
  - [Learning Outcomes](#learning-outcomes)
  - [What is the `typeof` Operator?](#what-is-the-typeof-operator)
  - [Using the `typeof` Operator](#using-the-typeof-operator)
  - [Where and When to Use the `typeof` Operator?](#where-and-when-to-use-the-typeof-operator)

## Learning Outcomes

After completing this topic, the student:

- Describes the usage of the `typeof` operator in JavaScript;
- Explains when and where to use the `typeof` operator;
- Uses the `typeof` operator to determine the type of variables and values.

## What is the `typeof` Operator?

The `typeof` operator is a JavaScript operator that returns the type of a given variable as a string. It can be used to determine the type of both variables and values.

## Using the `typeof` Operator

The `typeof` operator can be used as follows:

```javascript
const number = 123;
console.log(`${number} type is ${typeof number}`);
let age;
console.log(`Type of an uninitialized variable is ${typeof age}`);
const person = {
  firstName: 'John',
  lastName: 'Doe'
};
console.log(typeof person);
```

Output:

```bash
$ node app.js 
123 type is number
Type of an uninitialized variable is undefined
object

```

## Where and When to Use the typeof Operator?

Since JavaScript is a dynamically typed language, the type of a variable may not always be known or may not be what you expect. The typeof operator can be used to check the type of a variable and make decisions accordingly.

For example, if our application asks the user for their age, we typically expect them to input a number. However, the user might input text instead. If we then try to perform arithmetic operations on the age, we might get unexpected results.

To verify that the input value is of the expected type, we can use the typeof operator:

```javascript
const userInput = 25;

if (typeof userInput === 'number') {
  console.log('The entered value is a number');
  // Perform calculations with the age here
} else {
  console.log('The entered value is not a number');
  // Handle the situation where the user entered something else
}

```

[Source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof)

# Truthiness in JavaScript


- [Truthiness in JavaScript](#truthiness-in-javascript)
  - [Learning Outcomes](#learning-outcomes)
  - [What is Truthiness in JavaScript?](#what-is-truthiness-in-javascript)
  - [Truthiness Conversion](#truthiness-conversion)
  - [Logical Expression Table](#logical-expression-table)

## Learning Outcomes

After completing this topic, you will be able to:

- Define what truthiness is in JavaScript;
- Explain which values are coerced to true or false in JavaScript;
- Use a logical expressions table to determine if an expression is true or false.

## What is Truthiness in JavaScript?

When talking about truthiness in JavaScript, we refer to whether an expression is true or false. We use truthiness to check if an expression is true or false to make decisions. To check truthiness, we use comparison operators, which result in `true` or `false`. For example:

```javascript
console.log(5 > 3); // true
console.log(5 < 3); // false
```
What happens if we use a variable or a value that is not of boolean type in a conditional statement instead of a comparison operator and expression? For example:

```javascript
let number = 5;

if (number) {
  console.log('Number is true');
} else {
  console.log('Number is false');
}
```
Using the `if` conditional statement, we check whether the variable `number` is true or false. When we run the previous code, we see that the output is `Number is true`. But why? To understand why this is so, we need to understand how JavaScript converts variables to true or false.

## Truthiness Conversion

In JavaScript, every value can be converted to either true or false. When we use an `if` statement, JavaScript converts the variable to true or false to determine whether the code block should be executed or not.

In JavaScript, almost all values are converted to true, except for the following values:

The information below is presented in an Estonian markdown table format:

| Value         | Type      | Description                                                    |
|---------------|-----------|----------------------------------------------------------------|
| null          | Null      | Absence of value (intentional).                                |
| undefined     | Undefined | Absence of value (e.g., a variable that is declared but not assigned) |
| false         | Boolean   | The keyword false.                                             |
| NaN           | Number    | Not a number.                                                  |
| 0             | Number    | The number zero, including 0.0, 0x0, etc.                      |
| -0            | Number    | The negative number zero, including -0.0, -0x0, etc.           |
| 0n            | BigInt    | BigInt zero, including 0x0n, etc. Note: BigInt negative zero does not exist — the negation of 0n is 0n. |
| ""            | String    | An empty string value, including '' and ``.                    |
| document.all  | Object    | The only falsy object in JavaScript is the built-in document.all (in browsers). |

Other values are converted to true. For example:

```javascript
console.log(5); // true
console.log('Hello'); // true
console.log('0'); // true
console.log([]); // true
console.log({}); // true
console.log(-42); // true
```
Such behavior can be very useful when we want to check if a variable is defined and has a value. For example:

```javascript
if (username && password) {
  console.log('Username and password are defined');
} else {
  console.log('Username and/or password are undefined');
}
```
If we run the previous code, we will see that if the variables `username` and `password` are defined, the output will be `Username and password are defined`. If one or both variables are undefined, the output will be `Username and/or password are undefined`.

## Logical Expressions Table

As we already know, we can use logical operators to make decisions based on multiple expressions or values. Below is a table of logical expression truth values, where `A` and `B` are truth values, `&&` is logical AND, `||` is logical OR, and `!` is logical NOT.

| `A`     | `B`     | `A && B` | `A \|\| B` | `!A`   |
|---------|---------|----------|------------|--------|
| false   | false   | false    | false      | true   |
| false   | true    | false    | true       | true   |
| true    | false   | false    | true       | false  |
| true    | true    | true     | true       | false  |

For example, if we have the expression `A && B`, it is true if both `A` and `B` are true; otherwise, it is false. If we have the expression `A || B`, it is true if at least one of `A` or `B` is true; otherwise, it is false. If we have the expression `!A`, it is true if `A` is false. If `A` is false, then the result of the expression `!A` is true.

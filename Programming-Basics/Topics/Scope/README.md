# Skoop (_scope_)

![Skoop](Scope.webp)

*Image source: Dall-E by OpenAI*

**Skoop** (_scope_) is a concept that refers to where variables and expressions are accessible.

Scope is the current execution context in which values and expressions are "visible" or can be referenced. If a variable or expression is not within the scope, it is unavailable for use. Scopes can also be nested in a hierarchy, where a child scope has access to the parent scope but not vice versa.

JavaScript has the following types of scopes:

- **Global scope**: The default scope for all code running in script mode.
- **Module scope**: The scope for all code running in module mode.
- **Function scope**: The scope created by a function.

In addition, variables declared with `let` or `const` are subject to an additional scope:

- **Block scope**: The scope created by a pair of curly braces (a block).

A function creates its own scope, meaning variables defined within the function cannot be accessed from outside the function or by other functions. For example, the following is invalid:

```javascript
function exampleFunction() {
  const x = "declared inside function"; // x can only be used in exampleFunction
  console.log("Inside function");
  console.log(x);
}

console.log(x); // Causes error
```

However, the following code is valid because the variable is declared outside the function, making it global:

```javascript
const x = "declared outside function";

exampleFunction();

function exampleFunction() {
  console.log("Inside function");
  console.log(x);
}

console.log("Outside function");
console.log(x);
```

Block scope applies only to `let` and `const` declarations, not`var`:

```javascript
{
  var x = 1;
}
console.log(x); // 1
```

```javascript
{
  const x = 1;
}
console.log(x); // ReferenceError: x is not defined
```

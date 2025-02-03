---
marp: true
---

# Web Development


---

## Software Development

- Recap of the previous lecture
- Solving problems encountered during homework
- Github Issue
- .gitignore
- Branches, Pull Requests, and Merging
- Best Practices for Git and Github

---

## What did we talk about last time?

---

## Problems Related to the Lecture

- Poor visibility of the projector screen
  - From now on, we'll use the Live Share extension
- Very different skill levels
- Anything else?

---

## Problems Encountered During Homework

- Many typos and awkward phrasing - why?
- Specifics of Github Markdown
- Running code from the correct folder
- Anything else?

---

## Live Share Extension

- Live Share is a Visual Studio Code extension that allows multiple people to work on/view the same code file simultaneously.

---

## Installing Live Share

![Installing Live Share](https://github.com/FE-BE-Microdegrees/Subjects/blob/Slides-translation/Lessons/Common-Lessons/Lesson-02/image.png)

---

## Github `Issue`

- In the context of Github, an `Issue` is a feature that allows users to track tasks, bugs, and feature requests for a specific repository.
- An `Issue` can be open or closed.
- An `Issue` can be assigned labels, assignees, comments, and other attributes.

---

## How to Create an `Issue`

- Add a `collaborator` to your repository
- Create an `Issue` for your repository
- Assign the `Issue` to a `collaborator`

---

## `.gitignore`

- A `.gitignore` file is a file that specifies which files and folders to ignore in a repository.

---

## What is Added to the `.gitignore` File?

- Any files or folders you don't want to include in the repository.
- For example:
  - `.env` files
  - `node_modules` folders
  - `dist` folders
  - Files containing secrets

---

## `.gitignore` Exercise

- Create a `.gitignore` file for your repository
- Add the entry `draft.md` to the file
- `commit` and `push` your changes
- Add the file `draft.md` to your repository
- `commit` and `push` your changes
- What happened?

---

## Branches, Pull Requests, and Merging

- Creating branches
- Switching to a branch
- Working in a branch
- Creating a pull request
- Reviewing and merging a pull request
- Deleting a branch

---

## Branch Creation Process Exercise

- Create a new branch for your repository
- Make some changes in the new branch
- `commit` and `push` the changes
- Create a pull request
- Merge the pull request with the main branch
- Delete the branch

---

## Best Practices for Git and Github

- `commit` frequently
- Write meaningful `commit` messages
- Use a `.gitignore` file
- Do not add files containing secrets to the repository
- Use branches
- Sync frequently
- Always include a `README.md` file in the repository (also in subfolders)

---

## Programming

- Recap of the previous lecture
- Solving problems encountered during homework
- Operators and Expressions
- Conditional Statements

---

## What Did We Talk About Last Time?

---

## What Problems Did You Encounter During Homework?

---

## Operators and Expressions 1

- An operator is a symbol used to perform an action on one or more values.
- An expression is a combination of values, variables, operators, and functions that evaluates to a new value.

---

## Operators and Expressions 2

```javascript
let sum = 5 + 10;
```

- `5 + 10` is an expression
- `sum` is the variable name where the result of the expression is stored
- `+` is the operator
- `5` and `10` are operands

---

## Operators and Expressions 3

- Operators:
  - Arithmetic operators
  - Assignment operators
  - String operators
  - Comparison operators
  - Logical operators
    
---

## Arithmetic Operators

- `+` - addition
- `-` - subtraction
- `*` - multiplication
- `/` - division
- `%` - remainder

---

## Assignment Operators

- `=` - assignment
- `+=` - addition and assignment
- `-=` - subtraction and assignment
- `*=` - multiplication and assignment
- `/=` - division and assignment
- `%=` - remainder and assignment
- `++` - increment
- `--` - decrement
- `**` - exponentiation
- `**=` - exponentiation and assignment

---

## String Operators

- `+` - concatenation

---

## Comparison Operators

Comparison operators are used to compare two values and return a boolean value `true` or `false`.

- `==` - equals
- `===` - equals and is the same type
- `!=` - does not equal
- `!==` - does not equal and is not the same type
- `>` - greater than
- `<` - less than
- `>=` - greater than or equal to
- `<=` - less than or equal to

---

## Logical Operators

- `&&` - and (AND)
- `||` - or (OR)
- `!` - not (NOT)

---

## Conditional Statements

A conditional statement is a control structure used to make decisions based on a condition.

---

## Concepts Related to Conditional Statements

- Boolean expression

---

## Boolean Expression

A boolean expression is an expression that evaluates to either (`true`) or (`false`). It uses comparison operators.

A boolean expression can also be a variable whose value is either `true` or `false`.

The expression is used in conditional statements to decide whether or not to execute a block of code.

---

## Types of Conditional Statements

- `if`
- `if-else`
- `if-else-if`
- `switch`

---

## `if`

An `if` statement is used to execute a block of code if the condition is true

The syntax for an `if` statement is:

```javascript
if (condition) {
  // code to execute if the condition is true
}
```


## Example of `if`

```javascript
let weather = 'sunny';

if (weather === 'sunny') {
  console.log('I am going to the beach!');
}
```

---

## `if-else`

An `if-else`statement is used to execute one block of code if the condition is true, and another block of code if the condition is false.

The syntax for an `if-else` statement is:

```javascript
if (condition) {
  // code to execute if the condition is true
} else {
  // code to execute if the condition is false
}
```

---

## Example of `if-else`

```javascript
weather = 'sunny';

if (weather === 'sunny') {
  console.log('I am going to the beach!');
} else {
  console.log('I am going to the movies!');
}
```

---

## `if-else-if`

An `if-else-if`  statement is used when you need to check multiple conditions.

The syntax for an `if-else-if` statement is:

```javascript
if (condition1) {
  // code to execute if condition1 is true
} else if (condition2) {
  // code to execute if condition2 is true
} else {
  // code to execute if none of the conditions are true
}

```

---

## Example of `if-else-if` 

```javascript
let number = 5;

if (number > 0) {
  console.log('The number is positive');
} else if (number < 0) {
  console.log('The number is negative');
} else {
  console.log('The number is zero');
}

```

---

## Today's Homework

- Read through today's lecture materials
- Complete the exercises in the materials
- Upload your code for the exercises to Github

---

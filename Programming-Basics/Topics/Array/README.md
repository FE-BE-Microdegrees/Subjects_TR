# Array

In this chapter, we will discuss a data structure called an array. We will explore what an array is, how to use arrays, and how to manipulate them.

![Data Structures](Data-Structures.webp)

- [Array](#array)
  - [Learning Outcomes](#learning-outcomes)
  - [What is a Data Structure?](#what-is-a-data-structure)
  - [What is an Array?](#what-is-an-array)
  - [Array Methods](#array-methods)
  - [Adding Values to an Array](#adding-values-to-an-array)
  - [Searching for Values in an Array](#searching-for-values-in-an-array)
  - [Removing Values from an Array](#removing-values-from-an-array)
  - [Iterating Over an Array](#iterating-over-an-array)
  - [Exercises](#exercises)
    - [Exercise 1 - Basic Array Operations](#exercise-1---basic-array-operations)
    - [Exercise 2 - Array Iteration](#exercise-2---array-iteration)

## Learning Outcomes

After completing this topic, you will be able to:

- Define what a data structure is
- Define what an array is
- Use arrays
- Utilize basic array methods

## What is a Data Structure?

We already know what a variable is and how it is used to store data. However, so far, we have only been able to store a single value or describe a single thing using variables. For example, we might have a variable named `firstName` to store a person's **first name**. But what if we want to store a person's **first name**, **last name**, **age**, and **address**? We could create a separate variable for each, but this would be very inefficient. Instead, we can use a data structure to store all these values in a single variable.

A data structure is a way of organizing data in computer memory. Data structures are used to store collections of data.

JavaScript allows the use of the following data structures:

- Arrays
- Objects
- Maps
- Sets

> In this topic, we will focus on arrays.

## What is an Array?

An array is a collection of values stored in a single variable. Arrays are typically used to store collections of related data. For example, we can use an array to store a list of numbers or names.

To create an array, we use the `[]` operator. For instance, we can create an array named `numbers` containing the numbers `1`, `2`, and `3` as follows:

```javascript
const numbers = [1, 2, 3];
```

Or, we can create an array named `names` containing the names `John`, `Jane` and `Jack` as follows:

```javascript
const names = ["John", "Jane", "Jack"];
```

We can access the values in an array using their indices. The index of the first value in an array is `0`. For example, to access the first value in the `numbers` array, we use the index 0 as follows:

```javascript
const numbers = [1, 2, 3];

console.log(numbers[0]);
```

**Expected Output:**:

```bash
1
```

We can also change the value in an array using its index. For instance, to change the first value of the `numbers` array to`10`, we can use the index 0 as follows:

```javascript
const numbers = [1, 2, 3];

numbers[0] = 10;

console.log(numbers);
```

**Expected Output:**:

```bash
[10, 2, 3]
```

## Array Methods

Methods are functions associated with objects. This means that in JavaScript, we can perform operations on an object by calling a built-in function associated with it. Since arrays are essentially objects in JavaScript, they come with a variety of methods for manipulation.

For example, we can use the `push()` method to add a value to the end of an array, the `pop()` method to remove a value from the end, the `shift()` method to remove a value from the beginning, and the `unshift()` method to add a value to the beginning.

A comprehensive list of array methods is available in the [Array Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) ection of the MDN Web Docs.

## Adding Values to an Array

To add a value to the end of an array, we can use the `push()` method. For example, to add the number `4` to the end of the `numbers` array, we can use the `push()` method as follows:

```javascript
const numbers = [1, 2, 3];

numbers.push(4);

console.log(numbers);
```

**Expected Output:**:

```bash
[1, 2, 3, 4]
```

> Note that array methods are used in the form `massiiv.meetod()`.

## Searching for Values in an Array

To find the index of a value in an array, we can use the `indexOf()` method. For example, to find the index of the number `2` in the `numbers` array, we can use the indexOf() method as follows:

```javascript
const numbers = [1, 2, 3];

console.log(numbers.indexOf(2));
```

**Expected Output**:

```bash
1
```


## Removing Values from an Array

To remove a value from an array, we can use the `splice()` method. For example, to remove the number `2` From the `numbers` array, we can use the `splice()` method as follows:

```javascript
const numbers = [1, 2, 3];

numbers.splice(1, 1);

console.log(numbers);
```

**Expected Output**:

```bash
[1, 3]
```

## Iterating Over an Array

To iterate over an array, we can use a for loop. For example, to print each value in the days array on a new line, we can use a for loop as follows:

```javascript
const days = [
  "Esmaspäev",
  "Teisipäev",
  "Kolmapäev",
  "Neljapäev",
  "Reede",
  "Laupäev",
  "Pühapäev",
];

for (let i = 0; i < days.length; i++) {
  console.log(days[i]);
}
```

**Expected Output**:

```bash
Esmaspäev
Teisipäev
Kolmapäev
Neljapäev
Reede
Laupäev
Pühapäev
```

## Exercises

Create a file named index.js (or any name of your choice) and start adding solutions to the exercises below.


### Exercise 1 - Basic Array Operations

**Objective**: Add elements to an array and display them one by one.

*Description**: Create an array to store a list of three favorite fruits. Add two more fruits to the array using array methods. Finally, display each fruit on a new line.


<details>
  <summary>Solution</summary>

```javascript
const fruits = ["apple", "banana", "orange"];

fruits.push("strawberry");
fruits.push("pineapple");

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}

```

![Massiiv](array.gif)

</details>

### Exercise 2 - Array Iteration

**Objective**: Find the sum of all numbers in an array.

**Description**: Write a JavaScript program to create an array of numbers. Iterate over the array and calculate the sum of its elements. Print the final sum.



<details>
  <summary>Solution</summary>

```javascript
const numbers = [1, 2, 3, 4, 5];

let sum = 0;

for (let i = 0; i < numbers.length; i++) {
  sum += numbers[i];
}

console.log(sum);
```

**Expected Output**:

```bash
15
```

</details>

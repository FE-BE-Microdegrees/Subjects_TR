# Array Methods

![Array Methods](Array-Methods.webp)

Image Source: Dall-E by OpenAI

We have already encountered and used some [array methods](../Data-Structures/README.md#array-methods), but there are many more methods available for working with arrays.

- [Array Methods](#array-methods)
  - [`map()`](#map)
  - [`forEach()`](#foreach)
  - [`filter()`](#filter)
  - [`find()`](#find)
  - [`reduce()`](#reduce)
  - [`sort()`](#sort)
  - [`includes()`](#includes)

## `map()`

The `map()` method is used to create a new array from the elements of an existing array. It takes a function as an argument, which in turn takes an array element as an argument and returns a new element. The method returns a new array where each element is the value returned by the function.

```javascript
const numbers = [1, 2, 3, 4, 5];

const doubledNumbers = numbers.map(number => number * 2);

console.log(doubledNumbers); // [2, 4, 6, 8, 10]
```

In this example, an arrow function is used, which takes an array element as an argument and returns it multiplied by two.

The same code can also be written as:

```javascript
const numbers = [1, 2, 3, 4, 5];

const doubledNumbers = numbers.map(function(number) {
  return number * 2;
});

console.log(doubledNumbers); // [2, 4, 6, 8, 10]
```

## `forEach()`

The `forEach()` method is used to iterate over the elements of an array and perform some operation for each element. It takes a function as an argument, which in turn takes an array element as an argument. This method does not return anything.

```javascript
const numbers = [1, 2, 3, 4, 5];

numbers.forEach(number => console.log(number));
```

In this example, each element of the array is logged to the console.

While `map()` and `forEach()` are similar, the `map()` method returns a new array where each element is the value returned by the function, whereas the forEach() method does not return anything.

## `filter()`

The `filter()` method is used to create a new array from the elements of an existing array that satisfy a given condition. It takes a function as an argument, which in turn takes an array element as an argument and returns true or false. The method returns a new array with only those elements for which the function returned  `true`.

```javascript
const posts = [
  { title: 'Post 1', likes: 5 },
  { title: 'Post 2', likes: 10 },
  { title: 'Post 3', likes: 15 }
];

const popularPosts = posts.filter(post => post.likes > 10);

console.log(popularPosts); // [{ title: 'Post 3', likes: 15 }]
```

In this example, all posts with more than 10 likes are selected.

## `find()`

The `find()` method is used to find the first element in an array that satisfies a given condition. It takes a function as an argument, which in turn takes an array element as an argument and returns true or false. The method returns the first element for which the function returned true.

```javascript
const users = [
  { name: 'Alice', age: 25 },
  { name: 'Bob', age: 30 },
  { name: 'Charlie', age: 35 }
];

const user = users.find(user => user.name === 'Bob');

console.log(user); // { name: 'Bob', age: 30 }
```

In this example, the user with the name  `'Bob'` is found..

## `reduce()`

The `reduce()` method is used to compute a single value from the elements of an array. It takes a function as an argument, which in turn takes two arguments: the accumulator and the array element. The method returns the value of the accumulator.

```javascript
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((accumulator, number) => accumulator + number, 0);

console.log(sum); // 15
```

In this example, the sum of the elements in the array is calculated.

## `sort()`

The `sort()` method is used to sort the elements of an array. By default, it converts elements to strings and sorts them alphabetically. To sort numbers, you need to provide a function that compares two values and returns a negative value if the first should come before the second, a positive value if the second should come before the first, and 0 if they are equal.

> Note that the `sort()` method modifies the array itself and returns it.

```javascript
const names = ['Charlie', 'Alice', 'Bob'];

names.sort();

console.log(names); // ['Alice', 'Bob', 'Charlie']
```

In this example, the elements of the array are sorted alphabetically.

```javascript
const numbers = [3, 1, 2, 5, 4];

numbers.sort((a, b) => a - b);

console.log(numbers); // [1, 2, 3, 4, 5]
```

In this example, the array elements are sorted in ascending order using a custom compare function.

## `includes()`

The `includes()` method is used to check if an array contains a specific element. It returns true if the element is present, and false otherwise.

```javascript
const numbers = [1, 2, 3, 4, 5];

console.log(numbers.includes(3)); // true

console.log(numbers.includes(6)); // false
```

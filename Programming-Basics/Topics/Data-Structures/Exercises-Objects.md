# Additional Exercises for Objects

If you have completed the exercises in the learning materials but want to practice more, here are some additional exercises you can try. These exercises will help you practice using objects in different scenarios.

## Exercise 1: Counting Object Properties

**Description:** Create an object that contains different fruits and their quantities. Then write code that counts how many different types of fruits are in the object.

**Example:**

```javascript
const fruits = {
  apple: 5,
  banana: 2,
  orange: 7
};
```
**Output:** `3`

> **Hint:** You can use the [`Object.keys`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys) method to get the keys of the object as an array.

## Exercise 2: Sum of Object Values

**Description:** Given an object that contains the ages of different people, write code that calculates and outputs the sum of all the ages.

**Example:**

```javascript
const ages = {
  John: 25,
  Mary: 31,
  Chris: 16
};
```
**Output:** `72`

> **Hint:** You can use the [`Object.values`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values) method to get the values of the object as an array.

## Exercise 3: Filtering Object Elements

**Description:** Given an object that contains the prices of different products, write code that creates a new object that includes only the products with a price less than `10`.

**Example:**

```javascript
const prices = {
  book: 15,
  pen: 5,
  notebook: 8,
  pencil: 2
};
```
**Output:**

```plaintext
{
  pen: 5,
  notebook: 8,
  pencil: 2
}
```
> **Hint:** You can use the [`Object.entries`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries) method to get the keys and values of the object as an array.

### Exercise 4: Finding the Oldest Person in an Array of Objects

**Description:** Given an array of objects, each representing a person with `name` and `age` properties, write code that finds the oldest person in the array and outputs their name.

**Example:**

```javascript
const people = [
  { name: 'John', age: 25 },
  { name: 'Mary', age: 31 },
  { name: 'Chris', age: 16 }
];
```
**Output:** The oldest person is: Mary


markdown
Copy code
### Exercise 5: Combining Objects and Arrays

**Description:** Given an array of objects, each representing a book with `title`, `author`, and `read` (boolean indicating whether the book has been read or not) properties, write code that counts how many books have been read and how many are still unread.

**Example:**

```javascript
const books = [
  { title: 'The Hobbit', author: 'J.R.R. Tolkien', read: true },
  { title: 'Harry Potter', author: 'J.K. Rowling', read: false },
  { title: '1984', author: 'George Orwell', read: true }
];
```
**Output:** `2 read, 1 unread`

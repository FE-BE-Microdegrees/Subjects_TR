# JSON (JavaScript Object Notation)

![JSON](JSON.webp)

Image Source: [Dall-E by OpenAI](https://openai.com/)

- [JSON (JavaScript Object Notation)](#json-javascript-object-notation)
  - [What is JSON?](#what-is-json)
  - [Using JSON](#using-json)
  - [JSON.stringify()](#jsonstringify)
  - [JSON.parse()](#jsonparse)

## What is JSON?

JSON stands for *JavaScript Object Notation* and is a simple, human-readable data interchange format commonly used for transmitting data between client and server applications, such as between a web application's frontend and an API.

JSON data is represented as a collection of key-value pairs, where keys are strings and values can be strings, numbers, booleans, arrays, or other objects. JSON is easy for humans to read and write, and easy for machines to parse and generate. While JSON looks very similar to a JavaScript object, it is important to note that JSON is a data format, not a JavaScript object. The biggest difference is that JSON keys must always be enclosed in double quotes, whereas JavaScript object keys do not require quotes.

Here is an example of a simple JSON object:

```json
{
  "name": "John",
  "age": 30,
  "isStudent": true,
  "favoriteFoods": ["pizza", "sushi", "ice cream"]
}
```

In the above example, the object has four attributes: `name`, `age`, `isStudent` and `favoriteFoods`. The `name` and `isStudent` attributes are strings, the age attribute is a number, and the favoriteFoods attribute is an array of strings.

## Using JSON

JSON is frequently used in web applications for exchanging data between the client and server, such as with AJAX (Asynchronous JavaScript and XML) requests or for communicating with a web API. Many programming languages, including Node.js, have built-in support for reading and generating JSON data, making JSON a popular choice for web development.

Key characteristics of JSON:

- Simple and readable data exchange format.
- JSON objects are enclosed in curly braces: {"key": "value"}.
- JSON consists of key-value pairs separated by a colon: { "key": "value" }.
- Keys must be strings, and values can be strings, numbers, objects, arrays, booleans, or null.
- Key-value pairs are separated by commas: {"id": "1", "description": "Task completed"}.

## JSON.stringify()

`JSON.stringify()`  is a JavaScript function that converts a JavaScript object into a JSON string. This function takes an object as input and returns it as a JSON string.

Example of using `JSON.stringify()` :

```javascript
const person = {
  name: "John",
  age: 30,
  isStudent: true,
  favoriteFoods: ["pizza", "sushi", "ice cream"]
};

const jsonPerson = JSON.stringify(person);

console.log(jsonPerson);
```

Output:

```json
{"name":"John","age":30,"isStudent":true,"favoriteFoods":["pizza","sushi","ice cream"]}
```

In the example above, thet `person` object is converted to a JSON string using the `JSON.stringify()` function. The JSON string is stored in the `jsonPerson` ariable and then logged to the console.

`JSON.stringify()`is useful for converting JavaScript objects into JSON strings for data transmission or storage.

## JSON.parse()

`JSON.parse()` is a JavaScript function that converts a JSON string into a JavaScript object. This function takes a JSON string as input and returns it as a JavaScript object.

Example of using `JSON.parse()`:

```javascript
const jsonPerson = '{"name":"John","age":30,"isStudent":true,"favoriteFoods":["pizza","sushi","ice cream"]}';
const person = JSON.parse(jsonPerson);

console.log(person);
```

Output:

```javascript
{
  name: 'John',
  age: 30,
  isStudent: true,
  favoriteFoods: [ 'pizza', 'sushi', 'ice cream' ]
}
```

In the example above, the jsonPerson JSON string is converted to a JavaScript object using the JSON.parse() function. The resulting object is stored in the person variable and then logged to the console.

JSON.parse() is useful for converting JSON strings into JavaScript objects for data processing, such as when receiving data from an API or reading from a file.

Sources

- <https://www.json.org/json-en.html>
- <https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON>
- <https://google.github.io/styleguide/jsoncstyleguide.xml>

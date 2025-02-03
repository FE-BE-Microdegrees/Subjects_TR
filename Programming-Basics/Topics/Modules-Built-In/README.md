# Built-In Modules

![Built-In Modules](Built-In-Modules.webp)

Image Source: Dall-E by OpenAI

- [Built-In Modules](#built-in-modules)
  - [Learning Outcomes](#learning-outcomes)
  - [Importing Built-In Modules](#importing-built-in-modules)
  - [Using Built-In Modules](#using-built-in-modules)
  - [List of Built-In Modules](#list-of-built-in-modules)
  - [`fs` Module](#fs-module)
    - [Reading a File](#reading-a-file)
    - [Writing a File](#writing-a-file)
    - [Deleting a File](#deleting-a-file)
  - [`path` Module](#path-module)
    - [Creating a Path](#creating-a-path)
  - [`os` Module](#os-module)
    - [Operating System Information](#operating-system-information)
  - [Exercises](#exercises)
    - [Exercise 1](#exercise-1)
    - [Exercise 2](#exercise-2)
    - [Exercise 3](#exercise-3)

For an introduction to modules in JavaScript, refer to [Modules](../Modules/README.md).

In addition to user-created modules, JavaScript also provides built-in modules. These are modules included with Node.js by default and can be used without downloading or installing them.

## Learning Outcomes

After completing this topic, you will:

- Understand what built-in modules are in Node.js.
- Be able to import built-in modules.
- Be able to use built-in modules in Node.js.

## Importing Built-In Modules

To use built-in modules, they must first be imported. For example:

```javascript
const fs = require('fs');
```

As shown, built-in modules can be imported in the same way as user-created modules, but they do not require a specific path; just the module name is sufficient.

## Using Built-In Modules

Built-in modules are used in the same way as user-created modules.

For instance, to read the contents of a file, you can use the `fs` module:

```javascript
const fs = require('fs');

fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

In this example, the contents of the file `file.txt` are read and displayed in the console.

## List of Built-In Modules

Here are some built-in modules available for use:

- `fs` - File System module
- `path` - Path module
- `os` - Operating System module
- `util` - Utility module
- `events` - Events module
- `http` - HTTP module
- `crypto` - Cryptography module
- `zlib` - Compression module
- `stream` - Stream module
- ...

For a complete list of built-in modules, refer to the [official Node.js documentation](https://nodejs.org/dist/latest-v19.x/docs/api/).

## `fs` Module

The `fs` module is a built-in Node.js module that allows working with the file system. It supports reading, writing, modifying, and deleting files.

### Reading a File

To read a file, use the  `fs.readFile` method. For example:

```javascript
const fs = require('fs');

fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

You can also use the synchronous method `fs.readFileSync`:

```javascript
const fs = require('fs');

const data = fs.readFileSync('file.txt', 'utf8');
console.log(data);
```

> Note: Use synchronous methods only when you're certain it won't block other processes, as they may slow down the application.
> 
### Writing a File

To write to a file, use the `fs.writeFile` method. For example:

```javascript
const fs = require('fs');

fs.writeFile('file.txt', 'Hello, World!', (err) => {
  if (err) throw err;
  console.log('File has been written!');
});
```

You can also use the synchronous method `fs.writeFileSync` 

```javascript
const fs = require('fs');

fs.writeFileSync('file.txt', 'Hello, World!');
console.log('File has been written!');
```

### Deleting a File

To delete a file, use the  `fs.unlink` method. For example:

```javascript
const fs = require('fs');

fs.unlink('file.txt', (err) => {
  if (err) throw err;
  console.log('File has been deleted!');
});
```

You can also use the synchronous method `fs.unlinkSync`:

```javascript
const fs = require('fs');

fs.unlinkSync('file.txt');
console.log('File has been deleted!');
```

## `path` Module

The `path` module is a built-in Node.js module that helps with file paths and names. It allows creating, modifying, and analyzing paths to files and directories.

### Creating a Path

To create a path, use the `path.join` method. For example:

```javascript
const path = require('path');

const filePath = path.join(__dirname, 'file.txt');
console.log(filePath);
```

This example generates a path to the file `file.txt` using the `__dirname` variable, which points to the current directory.

## `os` Module

The `os` module is a built-in Node.js module that provides information about the operating system. It supports retrieving data such as the OS version, architecture, CPU details, username, and home directory.

### Operating System Information

To retrieve OS information, use methods provided by the os module. For example:

```javascript
const os = require('os');

console.log(os.platform()); // 'win32'
console.log(os.arch()); // 'x64'
console.log(os.cpus()); // [{ model: 'Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz', speed: 2808, times: { user: 0, nice: 0, sys: 0, idle: 0, irq: 0 } }]

// ...
```

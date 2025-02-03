# Third-Party Modules

![Third-Party Modules](Third-Party-Modules.webp)

Image Source: Dall-E by OpenAI

For an introduction to modules in JavaScript, refer to [Modules](../Modules/README.md).

In addition to user-created and built-in modules, Node.js also allows the use of third-party modules. These modules are created by other developers and are available through the *[Node Package Manager (NPM)](https://www.npmjs.com/)* registry.

- [Third-Party Modules](#third-party-modules)
  - [Learning Outcomes](#learning-outcomes)
  - [NPM](#npm)
  - [package.json](#packagejson)
  - [Installing Third-Party Modules](#installing-third-party-modules)
  - [The `node_modules` Folder](#the-node_modules-folder)
  - [Restoring the `node_modules` Folder](#restoring-the-node_modules-folder)
  - [Using Third-Party Modules](#using-third-party-modules)
  - [Removing Third-Party Modules](#removing-third-party-modules)
  - [Installing and Using a Third-Party Module](#installing-and-using-a-third-party-module)
  - [List of Useful Third-Party Modules](#list-of-useful-third-party-modules)
  - [Exercises](#exercises)
    - [Exercise 1](#exercise-1)
    - [Exercise 2](#exercise-2)
    - [Exercise 3](#exercise-3)
    - [Exercise 4](#exercise-4)

## Learning Outcomes

After completing this topic, you will:

- Understand what third-party modules are.
- Be able to create a `package.json` file.
- Know how to install third-party modules.
- Know how to use third-party modules.

## NPM

NPM, or Node Package Manager, is Node.js's package management system. It allows developers to download and use modules created by others. NPM comes bundled with Node.js and is accessed via the command line. Third-party modules are stored in the [NPM registry](https://www.npmjs.com/), which contains thousands of modules designed to solve various problems, such as:

- [Express](https://www.npmjs.com/package/express) - For creating web applications.
- [MySQL](https://www.npmjs.com/package/mysql) - For interacting with MySQL databases.
- [Axios](https://www.npmjs.com/package/axios) - For making HTTP requests.
- [prompt-sync](https://www.npmjs.com/package/prompt-sync) - For accepting user input in Node.js.

## package.json

To use third-party modules, a `package.json` file must be created in the project's root directory. This file contains the project's configuration and dependencies. Dependencies are modules used by the project. For instance, if your project uses the `prompt-sync` module, you need to add it as a dependency in the `package.json` file.

Create a `package.json` file using the following command:

```bash
npm init -y
```

This command generates a `package.json` file with default values:

```json
{
  "name": "project-name",
  "version": "1.0.0",
  "description": "Project description",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "Author name",
  "license": "MIT",
}
```

You can configure your project in detail by using npm init and following the prompts.

## Installing Third-Party Modules

Once a `package.json` file exists, third-party modules can be installed using the following command:

```bash
npm install <module-name>
```

For example, to install the `prompt-sync` module:

```bash
npm install prompt-sync
```

This command installs the `prompt-sync` module in the project's root directory and adds it to the dependencies list in `package.json` .

```json
{
  "name": "project-name",
  "version": "1.0.0",
  "description": "Project description",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "Author name",
  "license": "MIT",
  "dependencies": {
    "prompt-sync": "^4.2.0"
  }
}
```


## nThe node_modules Folder

Installed modules are stored in the  `node_modules`. folder in the project's root directory. This folder includes all project dependencies and their dependencies. It can grow large and is not recommended for version control (e.g., Git). Instead, add it to `.gitignore`.

 `.gitignore` example:

```plaintext
node_modules/
```


## Restoring the node_modules Folder

Restoring the node_modules Folder `node_modules` folder is not included in version control, other developers can recreate it using the following command in the project's root directory (where  `package.json`  is located):

```bash
npm install
```

This command generates the `node_modules` older based on the dependencies listed in `package.json`.

## Using Third-Party Modules

After installing a module, it can be used in code like any other module. For instance, using the `prompt-sync`  module:

```javascript
const prompt = require('prompt-sync'); // Import the module

const prompts = prompt(); // Initialize the module

const age = prompts('Enter your age: '); // Get user input

console.log(age); // Output the input

```

In this example, the `prompt-sync` module is used to prompt the user for their age and display it in the console.

## Removing Third-Party Modules

To remove an installed module, use the following command:

```bash
npm uninstall <module-name>
```

For example, to uninstall  `prompt-sync` :

```bash
npm uninstall prompt-sync
```

This removes the module from the `prompt-sync` folder and the dependencies list in `package.json`.

## Installing and Using a Third-Party Module

![Installing and Using a Third-Party Module](thirdPartyModules.gif)

## List of Useful Third-Party Modules

Here are some useful third-party modules:

- [Nodemon](https://www.npmjs.com/package/nodemon) - Automatically restarts Node.js applications.
- [prompt-sync](https://www.npmjs.com/package/prompt-sync) - For accepting user input.
- [colors](https://www.npmjs.com/package/colors) - For colored console text.
- [nodemailer](https://www.npmjs.com/package/nodemailer) - For sending emails.
- [cron](https://www.npmjs.com/package/cron) - For scheduling tasks.

## Exercises

### Exercise 1

Create a program that asks the user for a username and password. If the username is admin and the password is 1234, display Welcome!. Otherwise, display Invalid username or password!.

<details> <summary>Hint 1</summary>
Create a package.json file using npm init -y.

</details> <details> <summary>Hint 2</summary>
Use the prompt-sync module for user input. Install it with npm install prompt-sync.

</details> <details> <summary>Solution</summary>
  
  ```javascript
const prompts = require('prompt-sync');

const prompt = prompts();

const username = prompt('Palun sisesta oma kasutajanimi: ');
const password = prompt('Palun sisesta oma parool: ');

if (username === 'admin' && password === '1234') {
  console.log('Tere tulemast!');
} else {
  console.log('Vale kasutajanimi või parool!');
}

```

</details>

### Exercise 2

Enhance the program to allow the user to re-enter their username and password if incorrect.

<details> <summary>Hint</summary>
Use a loop (e.g., while) to repeat the input prompt until the correct credentials are provided.

</details>

### Exercise 3

Modify the program to limit the number of incorrect attempts to three. After three incorrect attempts, terminate the program with the message Too many invalid attempts!.

### Exercise 4

Add color to the program's outputs using the colors module. For example, display Welcome! in green and Invalid username or password! in red.

<details> <summary>Hint 1</summary>
Install the colors module using npm install colors.

</details> <details> <summary>Hint 2</summary>
Use methods like colors.green and colors.red for colored output:

</details>

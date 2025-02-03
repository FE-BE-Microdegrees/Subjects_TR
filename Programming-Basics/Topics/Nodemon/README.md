# Nodemon

![Nodemon](Nodemon.webp)

Image Source: [Dall-E by OpenAI](https://openai.com/)

- [Nodemon](#nodemon)
  - [Learning Outcomes](#learning-outcomes)
  - [What is Nodemon?](#what-is-nodemon)
  - [Installing Nodemon](#installing-nodemon)

## Learning Outcomes

After completing this topic, you will:

- Be able to explain what Nodemon is.
- Know how to install Nodemon.
- Be able to use Nodemon for Node.js application development.

## What is Nodemon?

`nodemon` is a command-line tool for Node.js that automates the development process by automatically restarting your Node.js application whenever code changes are detected.

When you run an application with `nodemon`, it monitors files in the directory for changes. If you save changes to a file, `nodemon` restarts the application automatically, saving you from manually stopping and restarting it every time you make an update.

Nodemon also provides configuration options to customize its behavior, such as ignoring specific files or directories and setting a delay before restarting the application.

## Installing Nodemon

You can install `nodemon` using the Node Package Manager (NPM). There are two main installation options:

### Global Installation

To install `nodemon` globally so it can be used across all projects, run the following command:

```bash
npm install -g nodemon
```
With a global installation, you can run nodemon from anywhere in your system without needing to install it in every project.

### Local Installation

To install nodemon as a development dependency for a specific project, use the following command:
```bash
npm install --save-dev nodemon
```
The --save-dev flag ensures that nodemon is listed as a development dependency in the project's package.json file. This means it is only installed when working in development mode and not included in the production environment.
### Running with Nodemon
After installation, you can use nodemon by replacing the node command with nodemon. For example:
```bash
nodemon app.js
```
This command starts your Node.js application with nodemon, which will monitor for changes and automatically restart the app as needed.
Reference:

- <https://www.npmjs.com/package/nodemon>

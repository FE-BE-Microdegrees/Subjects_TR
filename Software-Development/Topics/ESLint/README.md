---
marp: true
---

# ESLint

![Static Code Analysis](Static-Code-Analyzator.webp)

- [ESLint](#eslint)
  - [Learning Outcomes](#learning-outcomes)
  - [What is ESLint?](#what-is-eslint)
  - [Installing ESLint for a NodeJS Project (VSCode)](#installing-eslint-for-a-nodejs-project-vscode)
  - [Airbnb](#airbnb)
  - [Line Endings LF vs CRLF](#line-endings-lf-vs-crlf)
  - [Setting Line Endings in VSCode Editor](#setting-line-endings-in-vscode-editor)
  - [Setting the Number of Spaces](#setting-the-number-of-spaces)
  - [.eslintrc.js File Content](#eslintrcjs-file-content)

## Learning Outcomes

After completing this module, the student will:

- Describe ESLint and its benefits;
- Install ESLint for a NodeJS project;
- Configure ESLint to use the Airbnb style guide.

## What is ESLint?

ESLint is a popular open-source tool for static code analysis of JavaScript code. It is used to find and fix common coding problems and to enforce a consistent coding style across the project.

ESLint can be used in various environments, such as Node.js, web browsers, and React Native, and it supports different JavaScript syntaxes.

ESLint is highly configurable and can be customized to fit specific project requirements. It includes pre-defined rules that can be enabled or disabled, and it also allows for custom rules to be created. The rules cover many best coding practices, including variable declarations, function definitions, conditional statements, and more.

ESLint is often integrated with code editors and build tools such as VS Code, Atom, Sublime Text, and Webpack, which can provide real-time feedback on coding errors and enforce coding standards.

## Installing ESLint for a NodeJS Project (VSCode)

First, add the ESLint extension to VSCode (if it’s not already added). You can find it under the extensions tab or here: <https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint>

1. Install ESLint as a development dependency as follows:

```bash
npm install eslint --save-dev
```

1. Run ESLint setup from your project root::

```bash
npx eslint --init
```

> Pay attention - it’s - `npx`, not `npm`
>
> This command will ask you questions to configure ESLint for your project. You can choose a style guide to follow, specify the types of files you want to lint, and configure some rules. In the Programming I course, we use the `Airbnb` style guide.

Answer the questions as follows:

Question: `? How would you like to use ESLint? ...`  
Choice: `> To check syntax, find problems, and enforce code style`

Question::`? What type of modules does your project use? ...`  
Choice: `> CommonJS (require/exports)`

Question:: `? Which framework does your project use? ...`  
Choice: `> None of these`

Question: `? Does your project use TypeScript? »`  
Choice: `No`

Question: `? Where does your code run? ...`  
Choice: `> Node`

Question: `? How would you like to define a style for your project? ...`  
Choice: `> Use a popular style guide`

Question: `? Which style guide do you want to follow? ...`  
Choice: `> Airbnb: https://github.com/airbnb/javascript`

Question: `? What format do you want your config file to be in? ...`  
Choice: `> JavaScript`

Dependency question: `? Would you like to install them now?`  
Choice: `Yes`

Question: `? Which package manager do you want to use? ...`  
Choice: `npm`

And you’re ready to start coding :smiley:

## Airbnb

Airbnb is one of the most popular JavaScript style guides. It is a widely adopted style guide based on best practices, aiming to promote code consistency and maintainability. The Airbnb JavaScript style guide is maintained by the Airbnb team and is used by many developers and organizations worldwide.

The Airbnb JavaScript style guide covers various aspects of JavaScript coding practices, including indentation, variable naming, function declarations, conditionals, and more. It is available on GitHub and actively maintained, which means it is regularly updated to keep up with changes in the JavaScript ecosystem.

There are other popular style guides for JavaScript, including the Google JavaScript Style Guide and the Standard JavaScript Style Guide. These style guides have their own conventions and best practices, so you can choose the one that best suits your development needs and preferences. It’s important to note that adopting a style guide can help improve code quality, readability, and maintainability, and facilitate collaboration among developers working on the same codebase.

## Line Endings LF vs CRLF

The difference between LF and CRLF is how they represent line breaks in text files. LF represents a single line break, which is used in Unix, Linux, and macOS operating systems. CRLF represents two characters: a "Carriage Return" followed by a line break, and it is used in Windows operating systems.

Choosing the correct line-ending character is important as it can affect how a text file is interpreted by different programs. For example, if you create a text file with CRLF line endings on a Windows machine and then move it to a Linux machine, some Linux programs may not interpret the line breaks correctly, which can cause errors or unexpected behavior.

Similarly, if you create a text file using LF line breaks on a Unix or Linux machine and then move it to a Windows machine, some programs running on Windows may not interpret the line breaks correctly.

To avoid issues related to line-ending characters, it is recommended to choose the appropriate line-ending character based on the operating system or text editor being used and to ensure that a consistent line-ending character is used throughout the file. Some text editors and version control systems (like Git) have settings to automatically convert line endings to the appropriate format when working with files across different operating systems.

## Setting Line Endings in VSCode Editor

To set LF as the default line-ending in VSCode on Windows, follow these steps:.

1. Open VS Code and go to the `Settings`, menu by clicking the gear icon in the lower-left corner of the window.
2. In the settings search bar, type `files.eol` and press Enter. This should show the `End of Line` setting.
3. Click the dropdown next to `End of Line` and select `LF` or `/n` to set `LF` as the default line ending..

Now, when you create a new file in the VSCode code editor, it will use `LF` line endings by default.

> If you already have a file that uses `CRLF` ine endings, you can change the file's line endings by clicking the `CRLF/LF` button in the bottom-right corner of the VSCode window and selecting `LF`.

## Setting the Number of Spaces

VSCode's default number of spaces (when pressing the `TAB` key) is four spaces. The Airbnb ruleset specifies two spaces. To configure VSCode to use two spaces instead of four, follow these steps:

1. Open VSCode.
2. Click the gear icon in the bottom-left corner to open the Settings menu.
3. From the list, select "Settings."
4. In the search bar at the top of the settings tab, type "indent" to display settings related to indentation.
5. Under "Editor: Tab Size," you can change the tab size (i.e., the number of spaces the tab uses). By default, it is set to 4—this should be changed to 2.
6. From now on, indentation will use 2 spaces instead of 4.

Additionally, you can convert existing indentation (e.g., from tabs to spaces) by following these steps:

1. Open the file you want to edit in VSCode.
2. Click the "Spaces" or "Tab Size" button in the bottom-right corner of the VSCode window. This will open a small context menu.
3. If you want to change the indentation size, click "Indent Using Spaces" and select the desired number from the list.
4. Don’t forget to save your changes.

## eslintrc.js File Content

```javascript
module.exports = {
  env: {
    browser: true,
    commonjs: true,
    es2021: true,
  },
  extends: 'airbnb-base',
  overrides: [
  ],
  parserOptions: {
    ecmaVersion: 'latest',
  },
  rules: {
    'linebreak-style': 0,
  },
}
```

---
marp: true
---

# Web Development


---

## Software Development

- VS Code Extensions and Tips
- Using the Command Line (*terminal*)

---

## VS Code Shortcuts - Search

- `Ctrl (Cmd) + P` - Opens the quick search, allowing you to search for files in the project folder
- `Ctrl (Cmd) + F` - Opens the search within the current file
- `Ctrl (Cmd) + Shift + F` - Opens the global search across the entire project folder
- `Ctrl (Cmd) + H` - Opens the find and replace within the current file
- `Ctrl (Cmd) + Shift + H` - Opens the global find and replace across the project folder

---

## VS Code Shortcuts - Comments

- `Alt + Shift + A` - Toggle block comments on selected lines

---

## VS Code Shortcuts - Copy/Cut/Delete/Select

- `Alt (Option) + Shift + Up Arrow` - Copy selected lines upwards
- `Alt (Option) + Shift + Down Arrow` - Copy selected lines downwards
- `Ctrl (Cmd) + C` - Copies the current line (even if no text is selected)
- `Ctrl (Cmd) + X` - Cuts the current line (even if no text is selected)
- `Ctrl (Cmd) + Shift + K` - Deletes the line where the cursor is located (does not go to clipboard)
- `Ctrl (Cmd) + Shift + L` - Selects all occurrences where the cursor is located
- `Ctrl (Cmd) + D` - Selects the next occurrence where the cursor is located

---

## VS Code Shortcuts - Miscellaneous

- `Ctrl (Cmd) + Shift + E` - Opens the sidebar to see all project files and folders
- `Ctrl (Cmd) + Shift + X` - Opens the sidebar to see all extensions
- `Ctrl (Cmd) + Shift + P` - Opens the command palette to search for all VS Code functions (*Command Palette*)
- `Ctrl (Cmd) + Alt (Option) + Up/Down Arrow` - Adds multiple cursors up/down

---

## VS Code Extensions

- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) - For easier Markdown editing and preview
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - For automatic code formatting
- [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph) - Visualizes Git history graphically
- [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments) - Highlights comments based on their type
- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) - Starts a development server with live page reload
- [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) - Real-time collaboration with other developers
- [Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens) - Highlights errors and warnings in your code

---

## Code Snippets

Available as an extension or self-created:

`File -> Preferences -> Configure User Snippets`

---

## Code Snippets - Self-Created

```json
"Print to console": {
    "prefix": "cl",
    "body": [
        "console.log('$1');",
        "$2"
    ],
    "description": "Log output to console"
},
```
---

## Code Snippets - Extensions

JavaScript (ES6) code snippets

---

## Using the Command Line

---

## Command Line Usage - Windows

- `cd kaustanimi` - Moves from one folder to another;
- `cd ..` - Moves up one folder level;
- `dir` - Displays the folder contents;
- `mkdir kaustanimi` - Creates a new folder;
- `del` - Deletes a file;
- `echo` - Writes text to the console;
- `type failinimi` - Shows the contents of a file;
- `cls` - Clears the console;
- `exit` - Closes the console;
  
---

## Command Line Usage - MacOS/Linux

- `ls` - Lists the folder contents;
- `cd kaustanimi` - Moves from one folder to another;
- `cd ..` - Moves up one folder level;
- `mkdir kaustanimi` - Creates a new folder;
- `rm failinimi` - Deletes a file;
- `mv failinimi uusfailinimi` - Renames a file;
- `mv failinimi kaustanimi` - Moves a file to another folder;
- `cp failinimi kaustanimi` - Copies a file to another folder;
- `cat failinimi` - Displays the contents of a file;
- `touch failinimi` - Creates a new file;
- `clear` - Clears the console;
- `exit` - Closes the console;

---

## Git-i käsud

- `git clone` - Clones a project from a remote server to your local machine
- `git add .` - Stages all changes for the next commit
- `git commit -m "Muudatuste kirjeldus"` - Saves changes to the commit history
- `git push` - Pushes changes to the remote server
- `git pull` - Pulls changes from the remote server
- `git status` - Shows the current status of changes
- `git log` - Shows commit history
- `git branch` - Lists all branches
- `git checkout -b uusBranch` - Creates a new branch and switches to it
- `git merge teineBranch` - Merges another branch into the current one

---

## Programming

---

## Modules

---

## Modules - What?

A module is a JavaScript file that contains code that can be reused in other JavaScript files.

Modules are used to organize code into logical units that can be reused throughout the program.

Modules can include functions, objects, classes, variables, and other JavaScript code elements.

---

## Modules - Types

- Self-written modules
- Built-in modules
- Third-party modules

---

## Self-Written Modules

As the name suggests, these are modules we write ourselves to structure and reuse code.

To use self-written modules, they must first be exported and then imported into the relevant file.

---

## Self-Written Modules - Exporting

```javascript
const myModule = {
  myFunction() {
    // function content
  }
}

module.exports = myModule;

```

---

## Self-Written Modules - Importing

```javascript
const myModule = require('./moduleFileName');
```

---

## Self-Written Modules - Usage

```javascript
const myModule = require('./moduleFileName');
myModule.myFunction();
```

---

## Built-in Modules

Built-in modules are provided by JavaScript and can be used without additional installation.

---

## Built-in Modules - List

- `fs` - File system module
- `path` - Path module
- `os` - Operating system module
- `util` - Utility module
- `events` - Events module
- `http` - HTTP module
- `crypto` - Cryptography module
- `zlib` - Zlib module
- `stream` - Stream module
- ...

---

## Built-in Modules - Importing

```javascript
const fs = require('fs');
```

---

## Built-in Modules - Usage

```javascript
const fs = require('fs');

const file = fs.readFileSync('file.txt', 'utf8');
```

---

## Third-Party Modules

Third-party modules are written by someone else and can be used in your project.

---

## NPM - Node Package Manager

- A registry for Node modules
- <https://www.npmjs.com/>

---

## Third-Party Modules - `package.json` File

The `package.json` file contains all the project-related information, including third-party modules (dependencies).

---

## Third-Party Modules - Creating a `package.json` File.

```bash
npm init -y
```

---

## Third-Party Modules - Installation

```bash
npm install moduleName
```

For example:

```bash
npm install prompt-sync
```

---

## Third-Party Modules - Usage

```javascript
const prompts = require('prompt-sync');

const prompt = prompts();

const name = prompt('Enter your name: ');

console.log(`Hello, ${name}!`);

```

---

## `node_modules` Folder

All third-party modules are stored in the `node_modules` folder.

---

## `.gitignore` File

The `node_modules` folder should be added to the `.gitignore` file so it is not uploaded to the remote server.

---

## Creating a `.gitignore` File

```bash
node_modules/
```

---

## Reinstalling Dependencies

When copying your project to another machine, all dependencies need to be reinstalled.

```bash
npm install
```

---

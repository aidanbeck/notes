# ====Modules & Package Management====

### Why Use Modules?

a module focuses on performing specific sets of tasks/features.
It makes code cleaner and more reusable between projects.
It also makes collaboration easier, as people can work on separate modules.

You can also use libraries (external modules) from other developers.
Focus on building unique features rather than recreating what others have done for you.



### Custom Modules

CommonJS Modules
- For Node.js?
- module.exports
- require()

ES6 Modules
- export
- import

Single Responsibility Principle
- each module focuses on a specific task

Creating a Custom Module
```
 function add(a,b) { return a+b; }
 function sub(a,b) { return a-b; }
 
 module.exports =  { add, sub };
```
This makes add() and sub() available in other files.


**module.exports**
- an object in Node.js
- the public API of your module
- defines what should be accessible when imported
- every file in Node.js is a module by default
- if not exported, the functions remain private to their native file


**require()**
```
const mathHelpers = require('./mathHelpers');

let x = mathHelpers.add(10,5);
```
this is how you import in Node.js


Importing a Single Function / Object
```
module.exports = add;
```

```
const add = require('./mathHelpers');
let x = add(3,4)
```
useful if a module only contains one important thing
Can be a class, object, or anything.


Import Class Example
```
const Logger = require('./logger');
const log = new Logger(); //create new object of class
```

If you need to export 20 functions, all must be in module.exports
However, this may signify your module should be split into multiple
```
module.exports = {
 areaOfCircle: areaOfCircle,
 circumference: circumference,
 findRadius: findRadius,
 arcLength: arcLength
}
```

Naming Conventions
- be concise
- be specific
- intuitively reflect functionality
- use lowercase-module-names-like-this.
// why wasn't this used in the examples? They used camelCase instead.
// is a module name different than the file name?



### Using require()

require() connects modules through code
- called with file path or module name (module name??)
- custom modules
- core/built-in Node.js modules (fs, http, path)
- external modules installed through npm (express, lodash, readline-sync)

How It Works
- node determines module type
 - checks for built-in match
 - checks for ./ or ../ beginning
 - if neither, it assumes it is an npm package in node_modules
- for custom modules, node looks for index.js or a file with the specified name.
- node executes the inside of the file, collecting values within module.exports
- require() returns value of these exports, allowing for use.

Built-In Modules
optimized for performance
- fs: reading, writing, modifying files
- path: tools for working with directory paths
- http: creating http servers, requests, and responses
- os: information about the OS.
- crypto: encryption & hashing

fs
```
 const fs = require('fs');
 
 fs.writeFileSync('example.txt','Hello World!'); //creates file

 fs.readFileSync('example.txt','utf-8'); //returns content as string

 fs.existsSync('example.txt') //returns true if file exists

 fs.appendFileSync('example.txt', 'test'); //appends "test" to file

 fs.unlinkSync('example.txt'); //deletes file
```



### Modules & Package Management

Node Package Manager (NPM)
- node's default package manager
- modules here are called "node modules"
- has a registry of thousands of modules
- has a CLI for interacting with registry

Registry
- online database
- developers share reusable modules
- www.npmjs.com
 - search packages
 - usage statistics
 - documentation
 - author information
 - source code

**package.json**
- created when you initialize a node.js project (npm init -y)
- describes information about your project
- manages all external modules (dependencies)
- specifies scripts for automating tasks(???)
- ensure consistent builds across enviornments(???)

package.json Example
```
{
 "name": "my-project",
 "version": "1.0.0",
 "description": "A sample project to demonstrate package.json",
 "main": "index.js",
 "scripts": {
   "start": "node index.js"
 },
 "dependencies": {
   "readline-sync": "^1.4.9"
 }
}
```
- name: name of your project
- version: version of your project
- main: entry point of your project (default is index.js)
- dependencies: list of modules your project needs
- scripts: commands you can run with `npm run`

**npm install**
- allows anyone to download the exact same modules
- good for collaboration, you don't need to hunt down modules.

Version control
- ^ allows for minor changes (1.4.x)
- ~ allows for only patch updates (1.4.9 -> 1.4.10) //how is this different???
- no symbol locks dependency to specific version

Dependency
- a piece of code your project relies on to work
- usually a package/module

Scripts
within package.json:
```
 "scripts": {
 "start": "node index.js",
 "test": "jest"
 }
```
- `npm run start` will execute `node index.js`
- `npm run test` will execute the jest testing framework //how and why?

Initializing new npm Project
- `npm init -y`
- `-y` says yes to default settings

Install Any Node Module From npm
- find a module at www.npmjs.com
- install with `npm install module-name`, stored into node-modules

Dev Dependencies
- some modules are only needed during development, like jest
- they are called devDependencies
- to install a module as a devDependency, use flag `--save-dev`
`npm install module-name --save-dev`

Uninstall Module
`npm uninstall module-name`

Update Modules
- check for updates: `npm outdated`
- update all: `npm update`

Install All Dependencies At Once
- installs all modules listed in package.json
- this means you do not need to store node modules in git repository
`npm install`

Best Practices:
- keep custom modules close to main project files to simplify paths
- avoid deeply nested folder structures that make large paths
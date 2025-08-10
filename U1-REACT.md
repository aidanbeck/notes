==== JavaScript UI Libraries & React ====

**React has...**

Component-Based Architecture
- components encapsulate HTML *and* JS, making them more concise and portable.
- components are self contained
- components represent a specific piece of UI (button, form, menu)

Virtual DOM
- React targets only affected elements
- it doesn't reload the entire DOM Structure.

React Native
- can be used for mobile development
- good for porting websites, but other tools are better. Still, it has quick TTM

JSX (JavaScript XML)
- write HTML-like code directly within JS
- combine logic and structure
- concise and easy to visualize
- reduces switching between files

Ecosystem - Community Tools
- React Router: navigate between pages/views
- Redux: manage complex state
- Next.js: server-side(?) rendering and static site generation.
- React's active community ensures innovation, tools, resources, and support

Drawbacks & Limitations
- Added complexity from tools, state management, and advanced features
- Not a full framework, just UI.
- Simple libraries or JavaScript might be better for smaller scoped projects
- Updates and changes make keeping up difficult

When To Use
- Dynamic User Interfaces (dashboards, chats, live feeds) benefit from efficient rendering.
- Reusable & Scalable Code (projects that grow over time)
- Cross platform (ish)



# ==== Creating a React App & Its Components ====

Vite: a modern front-end build tool.
- scaffolds new React projects
- manages required dependencies
- provides a local development server

Initialize a New React Project
- bash: `npm create vite@latest`
- name project
- select React
- select JavaScript
- run what it tells you
- press h for useful shortcuts

Optional Setup:
- delete svgs
- wipe index.css and App.css
- set App.jsx to:
```
import './App.css';

function App() {

  return (
    <>
      <div>
      </div>
    </>
  )
}

export default App;
```


# File Structure

Root Level
- index.html: app's entry point
 - contains `<div id="root:></div>` where react renders app.
 - links src/main.jsx where app is initialized
- package.json: dependencies like in npm.
- vite.config.js: vite config
- .gitignore: preset gitignore
- node_modules/: npm dependencies
- public/: for static files that don't require Vite's processing
 - images, favicon, anything served as is.
 - what decides this? how is this different than src/assets/?

The src Directory - most work takes place here
- main.jsx: React's entry point. renders App.jsx into index.html's root div.
- App.jsx: root component. Your App begins here.
- App.css: styles App.jsx. Global stylesheet for your app.
- assets/: contains static assets like images, icons, media files.


# React Components

Best Practices
- each component is its own file.
- component files exist in a components directory within src/
- each component is imported and used by the App component.

Functional Components
- simple JavaScript functions that return HTML written as JSX
- modern and lightweight
- "Hooks" allow you to manage state and lifecycle methods
src/components/SchnucksInfo.jsx:
```
function SchnucksInfo() {
 return (
 <div> Shnucks Info </div>
 );
}
export default SchnucksInfo;
```
Import into App.jsx:
```
import SchnucksInfo from './components/SchnucksInfo';
function App() {
 return (
  <div>
   <SchnucksInfo />
  </div>
 );
}
export default App;
```

Class Components
- legacy, from before Hooks arrived in 2018
- classes that extend React.Component
- include render() method that returns component's JSX
- don't have useState and useEffect methods.
```
import React from 'react';
class DierbergsInfo extends React.Component {
 render () {
  return (
   <div> Dierbergs Info </div>
  );
 }
}
// does it need to export?? No because it's not an object?
```
Import into App.jsx: identical to functional components

Note: React components need a single parent element that contains everything.
Each component file should export the component so it can be imported and used elsewhere.



# ==== Leveraging JSX for Dynamic Web Interfaces ====

Incorporating JavaScript Expressions into JSX
- embed JS with `{}`
- display variable: `<h1>Welcome, {userName}!</h1>`. userName string is dynamically injected into the tag.
- calculations: `<p>The sum is: {num1 + num2}</p>`
- call functions: `<h1>{getGreeting("Alex")</h1>`

Conditional Rendering
- render elements based on if statements and ternary operators
- ternary operator: `const greeting = <h1>{isLoggedIn ? "Welcome back!" : "Please log in."}</h1>`
 - good for true/false
 - concise
- render an element if a condition is true: `const notifMsg = hasNotifs && <p>you have notifs!</p>;`
 - concise
 - how *exactly* does this work?
- if statements: work as you'd expect. assign different value to JSX variable depending on condition.
 - complex conditions

Reviewing .map()
- is an array method made with optimized native code.
- this is my JavaScript translation of what it does.
```
array.map(inputFunction) {
 
 let newArray = [];

 for (let i = 0; i < array.length; i++) {
  newArray[i] = inputFunction(array[i],i);
 }
 
 return newArray;
}
```
- it takes a function as input (anonymous or not)
- it creates a new array, the same size as the original array
- it iterates over the original
 - for each index, it sets newArray[i] = inputFunction(original[i], i);
- it returns the newArray
- in english, it runs off an array and takes a function as input
- it returns a new array where each value equals input(value,index) of the OG

Creating Lists With .map()
```
const fruits = ["apple", "banana", "pear"];
const fruitList = fruits.map( 
 (fruit, index) => <li key={index}> {fruit} </li> //one line anonymous function
);
const element = <ul>{fruitList}</ul>;
```
- `.map()` iterates over `fruits` array
- `key` attributes are essential for React to track changes(what exactly is it doing?)
- JSX can be created inline
- the array of JSX can be created compiled into an element variable on the last line
 - what *exactly* is the JSX data type? how can an array of it be seamlessly added? how is it stored?

Understanding JSX with Experiments
- a variabled defined with JSX is compiled into an object of a unique class
 - I don't know what react calls this class, I am nicknaming the class "JSXobject"
- it is *not* creating an element object. You can not use element methods or attributes.
- nested HTML in jsx creates a JSXobject with children, other JSX objects.
- javascript within JSX using {} is run *at variable definition*.
 - it puts the output of the js into the class right then
 - it has no memory of the logic it used to get that value
- arrays of JSX are saved as normal arrays of JSXobjects.
- however, using {} to inject an array of JSXobjects has interesting properties.
 - it loops through the array, converting everything to a JSX object
 - it even goes into nested arrays
 - it returns JSX objects that are all of those it found together.
  - perhaps, it adds the array of JSX objects to it's parent?
  - or injects them between children if there are already children?

Rendering an Array of Objects
```
const users = [ {id:1, name"Alice"}, {id:2, name:"Bob"} ];
const userList = users.map(
 user => <li key={user.id}> {user.name} </li>
);
const element = <ul> {userList} </ul>
```

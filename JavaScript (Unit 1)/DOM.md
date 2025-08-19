# ==== The DOM and Browser APIs ====

Dynamic Web Pages
- change content/appearance after they've loaded
- based on user interactions or other events
- rely on the Document Object Model

Browser APIs
- interact with & modify the DOM
- document.getElementById()
- document.querySelector()

JavaScript Engines
- Different browsers run JS their own way
- Firefox uses SpiderMonkey
- Chrome uses V8
- caniuse.com checks compatibility

Inline JavaScript
- embed between \<script> tags
- useful for small scripts or experimentation

External
- link using `<script src="filepath">`
- reusable
- organizable & maintainable

Placement of `<script>`
- if a script tag runs before the DOM elements load, it will fail to interact with those elements.
- you can place `<script>` at the bottom of the `<body>` element to circumvent this.
- this is best for inline scripts
- you can place `<script>` in the `<head>` tag using the `defer` attribute. It waits to run until the DOM loads.

`<script src="script.js" defer></script>`
- `defer` allows for better organization. You can link js files and css files in the same area.
- it is best for external scripts

# Selecting Content with Browser APIs

.textContent vs .innerHTML
- .textContent updates the plain text
- .innerHTML can update tags and formatting too.

document.querySelector()
- selects *first element* that matches a CSS selector
- the input is the css selector itself, exactly how it's used in CSS
- element, `#id`, `.class`

Caching Elements
- .getElementById() and .querySelector() searches through the entire DOM tree - expensive!
- when we can, we should store the element's reference for later use (cache it)
- it is also maintainable and clean to use a clear variable name to refer to an element.
`const myElement = document.getElementById("my-element");`
- const is used because the element reference is unchanging.
- the element itself can still be changed.

Adding Elements
- create with     `const newElement = document.createElement("p");`
- add to DOM with `document.body.appendChild(newElement);`
- can you not do `let e = new Element;`?
- can you add to other things like `document.head`?
- where does a created but not appended element exist?

Removing Elements
```
const heading = document.getElementById("main-heading");
heading.remove();
```

Styling
- use `.style.backgroundColor` to alter css styling rules.
- is the style rule changed from kebab-case to camelCase?
- what is the rule priority compared to inline css?



# ==== Event Handlers ====

element.addEventListener(eventType, handlerFunction);
- element: the DOM element you want to attach the listener to
- eventType: string representing event to listen to. "click", "mouseover", "input".
- handlerFunction: the function to execute upon event
 - can be anonymous or existing function
 - doesn't need the ()'s, it passes an event variable by default (fact check?)

button.removeEventListener("click", handleClick);
- requires the same function reference as the addEventListener
- good for performance to remove unneeded events

==== What is JSON ==== (And Others)

JSON: Java Script Object Notation
- readible
- language agnostic
- key value pairs

Structure
- Objects {} for key-value pairs
- Keys "" enclosed in double quotes
- Values
 - Null
 - Numbers
 - Booleans
 - Arrays []
 - Strings (must be enclosed in double quotes)
 - Nested Objects { "obj": {} }

Not Allowed
- Functions
- Comments
- References

Common Uses
- APIs, languageless communication
- Config, readible & editable files

Common Errors in JSON
- Missing/Extra commas
- Improper quotation marks (missing or single quotes)
- Unmatched brackets/braces
- Trailing commas (not allowed at the end of arrays or objects)
- Incorrect data types
Use online validators like JSONLint or CodeBeautify to check
Use Shift + Alt + F to format JSON in VSCode
Use JS to Check
```
const data = '{"name": "Alice", "age": }'; // Invalid JSON
try {
   JSON.parse(data);
} catch (error) {
   console.error("Error parsing JSON:", error.message);
}

```



==== Sending & Recieving JSON Data ====

# Hyper Text Transfer Protocol - HTTP
Requests - GET & POST

Fetch Function
- fetch() takes a URL as an input and sends an HTTP GET request to it.
- The API processes the request and send back a response
- .then() takes a function as an input.
- It runs this function, inputting what the API sent.
- This function can then handle the data however you want.
```
fetch("https://example.com/file.json").then(
 function(response) { console.log(response); } // can also be non-anonymous
);
```

Network Dev Tool
- In the network tab you can see fetch requests.
- the "Name" is the name of the file returned(?)
- Click on the name to view fetch information (GET method, other stuff)
- This seems useful and interesting, I should look more into this!!!

Response Object
- instance of the Response Class
- wraps the API's data
- provides methods to access information about the request and data
- .json() is one such method. It extracts data and converts it to a JS object
- .catch() is used to catch errors after .then()'s //!!! see errors and debugging
// how does .then() work exactly? is it a universal method? can you do `(true).then(detectBoolean);`?

Updating Page With DOM & JSON Data
- you can use methods like .innerHTML to stitch data into the page.
- `element.innerHTML = `<em>{$json.text}</em>`;

Older Request Methods
- .fetch() is the modern standard
- be aware that older systems may use older techniques
- jQuery.get
- jQuery.ajax
- XMLHttpRequest API


# Asynchronous Programming & Promises

HTTP Requests are Asynchronous
- Asynchronous: Events that don't happen at the same time or in a set order.
- Synchronous: Events that occur simultaneously or in a sequential order.
- requests take a variable amount of time, depending on network speed, server location, and data size.
- the browser does other things (rendering, interactions) while waiting.
- .then() allows you to handle a response when it arrives.

Asynchronous Javascript And Xml - AJAX
- JSON has replaced XML as a standard, but the AJAX acronym predates that.

Promises
- fetch *actually* returns an instance of the "Promise" class.
- a "promise" represents the eventual outcome of an async operation.
- you can assign fetch to a variable
```
const fetchPromise = fetch("url");
fetchPromise.then(whatever);
```
- the .then() function runs whenever the promise finishes
- so, does .then() add the function to the promise variable, setting it as what runs later?
- promises can be filled or rejected. .then() defines behavior when it is fulfilled
- .json () *actually* returns a promise that resolves when data is converted to JSON
- so is .json() asynchronous? Answer: yes. Question: Why???

- .then is a method of the Promise class that allows us to run code after an event is completed
-Promises are used to represent the outcome of any asynchronous event in your code, such as HTTP requests, file reading, or timers. They provide a way to handle the result of these events once they are completed.

I would like to reorganize this file. I want it to start with the promise and response class, and then go into methods of the class.

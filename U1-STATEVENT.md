==== React Props ====

Props ("Properties")
- fundamental React concept
- pass data from parent to child component
- let components recieve information on what they should display/process
- read only, children cannot change its data
- pass data downstream, not upstream

Props can carry:
- primitives (strings, numbers, booleans)
- Arrays & Objects
- Functions (useable by the child, triggers actions in the parent)
 - doesn't this let you pass data upstream?

# How Props Work

Passing Props from a Parent Component
- they are like custom attributes
- `<Greeting name="Alex" />` (inside the parent component, where child exists)
- `name` is the key for the prop
- `"Alex"` is the value assigned to `name`

Receiving Props in a Child Component
- access through the built in `props` object.
- pass `props` an argument to the component function to access it's props.
- then, you can use `props.name` where name is the key to access that key's value.
// is `props` just the default first input into the function, and can you name it anything?
```
function Greeting(props) {
 return <h1>Hello, {props.name}!</h1>
}
```
Then, in the parent, you can use: `<Greeting name="Alex" />`

Benefits
- this allows you to reuse components in multiple places
- makes them like functions with inputs
- makes them like built in html elements with their own attributes
- lets the parent handle logic & state management
- lets the child be simple and just render what it's told



==== React Forms and State ====

State
- built in feature for remembering information
- essential for updating user information
- efficiently interface with React UI
- forms are crucial alongside state

How State Works with React
- does not automatically exist in every component
- you (the dev) need to explicity define & manage it.
- local variables in a function won't retain their values.
 - they also won't re-render when updated.
- use "state variables", created and managed using React's useState hook.

useState
- declare state variables
- takes an input: the initial state value
- returns two values:
 - current state
 - a function to update that state
`const [federalTax, setFederalTax] = useState(defaultTax);`
// whoa. what is this syntax? is this useable in all js?

Using Objects in State
- state variables can hold complex data types like arrays and objects
`const[taxes, setTaxes] = useState({ federal: 0, state: 0 });`
- then, if you *just* want to update state tax:
setTaxes( { federal: taxes.federal, state: -10 } );
- you have to send a whole new object through, but you can copy values over using the state variable
// could you use the ... operator?

State Persistence
- state resets when the page reloads
- to maintain between loads, you need backend or local browser storage


# Forms in React

In traditional HTML forms, the browser handles form data
In react, forms are not static elements.
They are dynamic components, and interact with the application's state
Controlled Forms: forms where the input values are managed by react's state

Controlled Forms
- react's state is the single source of truth for the input values
- each form element (text input, checkbox) is bound to 1 variable.
- any changes to the form are reflected in state.
This is done by
- binding the form element's value attribute to a state variable
- using an onChange event handler to update state when the user interacts

Why use Controlled Forms
- real time updates
- data validation
- programatically reset/prefill fields by modifying state

# Creating a Controlled Form

Setting up a State
- create state variables for the form fields
```
import { useState } from "react";

function UserForm() {
 const [email, setEmail] = useState("");
 
 return (
  <div>
   <h1>User Form</h1>
   {/* Form Goes Here */}
  </div>
 );
}

export default UserForm;
```

Binding Input Fields to State
```
<form>
 <label> Email
  <input type="email" value={email} onChange={ (e) => setEmail(e.target.value) }/>
 </label>
</form>
```
- `value` must be set to the state variable.
- `onChange` is used to access the state change function.
- `e` reprevents the event object, and contains the changed `value` variable.
- `type="email" is unimportant for state, it just means that the input has built in restrictions. could equal 'text'".

Display Form Data Automatically
`<p>Email: {email}</p>`
- nothing else needs to be done.
- this element will update with state automatically.

Avoid Inline Logic
- What we just did is bad practice.
- Instead, write your own function and pass it to onChange with jsx.
```
const handleNameChange = (e) => {
 setName(e.target.value);
}
...
<input value={name} onChange={handleNameChange}/>
```
- inline logic is harder to read when there are multiple large forms
- seeing `(e) => setName(e.target.value)` within jsx can be confusing.
- inline functions are not reusable, and maintaining duplicates is difficult.
- expanding the logic of a function is messier inline.
- performance: when inline is used, a new function is created *every* time.
- lets you console.log easier, helping debugging.

# Writing a Dynamic handleChange Function in REACT
- using seperate handlers is messy!
- Consolidate them into a single `handleChange` function.
- This handler will change state variables based on the input's `name` attribute.

Update to Use an Object
`const [formData, setFormData] = useState({ name:"", email:"" });`
- this contains all state data for the form.

Create `handleChange` Function
```
const handleChange = (e) => {
 const { name, value } = e.target; // makes code readible. this grabs e.target.name and e.target.value, and lets you use them as just `name` and `value.
 setFormData( (prevData) => ({...prevData, [name]: value }) ); // grab the defined "name" (meaning key) of the key value pair the input should change.
                                                               // then, it changes THAT value to the value of the input element.
};

Add `name` Attribute to Input Fields.
`<input type="text" name="name" value={formData.name} onChange={handleChange} />`
- In this case, the value of the name attribute is the key of the variable the element is targeting and will change within formData.
- This philosophy, instead of using a unique handler function, passes a special "targeted key" prop to a single handler function.

Benefits To This Fuckery
- adding a new field only requires adding a new formData key, and a `name` attribute to target that key



==== Conditional Rendering ====

Uses
- Personalization: Tailor the site to preferences, actions, or permissions
- Usability: Provide feedback, guide the user
- Performance: Only render necessary elements
- Responsiveness: Feel alive by changing based on actions/data


# Techniques For Conditional Rendering

If Statements
```
//within component function:
if (isLoggedIn) {
 return <h1>Welcome Back!</h1>;
} else {
 return <button>Login</button>;
}
```
- component functions allow for multiple return options.
- good for returning entirely different things, can do any comparisons

Ternary Operators
```
return (
<div>
 {isLoggedIn ? ( <h1> Welcome Back! </h1> ) : ( <button onclick={ () => setIsLoggedIn(true) }> Login </button> ) }
</div>
);
```
- concise
- great for boolean conditons
- good for rendering within jsx

Logical AND (&&) Operator
```
return (
<div>
 {isLoading && <p>Loading...</p>}
</div>
);
```
- render only when a condition is true
- render when there is no "else", it just doesn't render.
- how this works (I assume) is that if the first condition is true, it checks the second condition by rendering it.
- If the first condition is false, it doesn't check the second and therefor doesn't render it.
- bit of a hack, but it's concise

Scenarios:
- display a spinner when fetching api data
- display different pages if a user is logged in or not
- display error messages without cluttering ui when everything is fine
- toggle features on or off in app settings.
- change themes
- change based on mobile vs desktop
- display a multi step process one step at a time



==== URL Parameters with React Router ====

React Router
- a popular library for handling routing
- change the url
- extract data from the url

How Url Parameters Work
`site.com/product/123`
- `/product` represents the static part
- `123` is dynamic and can vary, representing a specific product id
- you should be able to fetch this product from a database.


# Setting Up React Router
`npm install react-router-dom`

Core Components
- Router: wraps your ENTIRE application to enable routing.
- Routes: Defines all the available routes in your app.
- Route: Specifies a path and the component to render when the path matches.

Example
```
import { BrowserRouter as Router, Route, Routes } from "react-router-dom";
function App() {
return (
 <Router>
  <Routes>
   <Route path="/product/:id" element={ProductPage/>} />
  </Routes>
 <Router>
);
}
```

Defining Dynamic Routes
- "Dynamic Routes" include placeholders for parameters.
- they are defined using a `:` before the parameter name
- `product/:id`
- the id gets passed to the component defined with `element`


Accessing URL Parameters
- use the useParams hook provided by React Router
```
import { useParams } from "react-router-dom";

function ProductPage() {

 const { id } = useParams(); //same as const id = useParams().id;? yes, verified.

 return (
  <div>
   <h1>Product ID: {id}</h1>
  </div>
 );
}

export default ProductPage;
```

Missing Parameter
- if a parameter is missing or not defined, you can provide a default message
- `const post Content = blogPosts[postId] || "Post Not Found.";

Validate Parameters
- `if (!blogPosts[postId]) {  return <p>Error</p>; }

Nested Routes
```
<Route path="/product/:id" element={<ProductPage/>}>
 <Route path="reviews" element={<ProductReviews/>}/>
</Route>
```
- how does this work?
- how do you have a custom element that contains another custom element?
- where is ProductPage rendered vs ProductReviews?
- is it just conditonal? if the route is nested it just goes further to another component?

Query Parameters
- parameters which follow a ? in the url
- `/search?term=react`
```
const query = new URLSearchParams(useLocation().search);
const searchTerm = query.get("term");
```
- What is this doing???

Useful Repo: https://github.com/aidanbeck/practice-taskManagement-Aidan-B



==== React Hooks ====

Hooks add stateful logic & advanced functionality to functional components

Common Hooks
- useEffect: fetch data, update DOM, subscribing to events
- useRef: precise reference/persist values across renders w/o rerendering. Track timers or input fiels
- useParams: access URL parameters to determine what data should display


# useEffect
- for side effects: outside the REACT render cycle
- fetching data from an API
- manually updating the DOM (should you do this?)
- subscribing to / cleaning up event listeners
Two Arguments
- callback function: define logic for the side effect
- dependency array (optional): define when the effect should re-run.
 - leave blank to run once
 - the array contains "dependencies", and the effect will re-run whenever they change
 - Later Notes on Dependency Arrays:
  - a dependency array ensures the effect only runs when specific values change
   - does it run each first render too?
  - a blank array ensures the effect runs only once
   - does no array make it run every render? 
 // what are dependencies in this case? state variables?
 A: dependencies are values, I assume any value or state values.
```
useEffect( () => {
 //logic
}, [dependencies]);
```
Fetching Data:
```
import {useState, useEffect } from "react";

function UserProfile() {
 const [user, setUser] = useState(null);
 
 useEffect(() => {
  fetch("example.com/users/1")
  .then( (response) => response.json() )
  .then( (data) => setUser(data) );
 }, []);

 return (
  <div>
   {user ? (
    <h1>{user.name}</h1>
    <p>{user.bio}</h1>
   ) : ( <p>Loading...</p> )}
  </div>
 );

}
```
- This displays a loading message as it waits for data from an api
- when it recieves that data, it updates the page with it using the setValue function
- if dependencies are defined, it will re-run the logic whenever those values change.


# useRef
- "get a reference to a DOM element"
- "access & persist values across renders" //what?
- storing mutable (alterable) values, like timers
// am I right to say this tracks state without causing re-renders?
How It Works
- returns object with a .current property
- you may update .current without affecting the render cycle
```
import { useRef } from "react";

function FocusInput() {
 
 const inputRef = useRef(null);
 
 const handleFocus = () => {
  let elementReference = inputRef.current;
  elementReference.focus(); //focus the input field
 };

 return (
  <>
   <input type="text" ref={inputRef}/>  // is `ref` built in? does this set inputRef.current?
   <button onclick={handleFocus}>Focus</button>
  </>
 );
}

export default FocusInput
```

useParams and Combining the Hooks was covered, but I didn't take notes on them.

I am shaky on the last hooks section, I should return to review and seek more explanations
On the purpose and workings of react hooks.

Useful Repo: https://github.com/aidanbeck/practice-taskManagement-Aidan-B
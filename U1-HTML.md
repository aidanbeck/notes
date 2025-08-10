# ==== An Introduction to HTML ====

How Web Pages Are Rendered
- browser sends a request from web server for the page.
- server responds with that page's code.
- browser interprets code and renders the page.

HTML is composed of ELEMENTS and TAGS

Elements
- organize content by type
- <element type>content</element type>

Tags
- define the type of content an element contains.
- specific instructions on how the browser should process it.
- <tag></tag>

Void Tags
- elements with no content
- require no closing tag
- typically insert standalone content
- <img>

Appropriate Tags
- use tags logically
- not just based on appearance
- use `<p>` for paragraphs
- use `<h1>` and `<h3>` for their correct hierarchy
- use `<header>` for introductory content at the top of a page/section
- this encourages collaboration and maintainability

Boilerplate
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- ^This makes web page responsive -->
    <title>My First HTML Page</title>
</head>
<body>
    <h1>Welcome to HTML!</h1>
    <p>This is the starting point for creating static web pages.</p>
</body>
</html>
```

VSCode Shortcut
- open new file
- type !
- press tab/enter
- VSCode will create boilerplate


Unordered List
```
<ul>
    <li></li>
    <li></li>
</ul>
```
Ordered List
```
<ol>
    <li></li>
    <li></li>
</ol>
```

Forms - collect info and send to server
```
<form action="/submit" method="POST">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
    <button type="submit">Submit</button>
</form>
```

Hierarchy
- use one `<h1>` per page.
- don't skip levels
- use css to change sizes

Tables
```
<table border="1">
    <caption>Employee Directory</caption>
    <tr>
        <th>Name</th>
        <th>Age</th>
        <th>City</th>
    </tr>
    <tr>
        <td colspan="2">Jane</td> (???)
        <td>28</td>
        <td>New York</td>
    </tr>
    <tr>
        <td>John</td>
        <td>35</td>
        <td>Los Angeles</td>
    </tr>
</table>
```
Use to structure data, not for page layout.

Semantic HTML
- div and span are non-semantic, use if no other fits
- semantic tags improve accessibility and SEO
- use `<header>` and `<nav>` for main top
- use `<section>` to define thematic groupings
- use `<article>` to reference self contained articles like blog posts that can stand alone.
- use `<aside>` for tangential information, like a sidebar or seperate fact.
- use `<footer>` for the footer and copyright information


Ultimate Boilerplate
```
<!DOCTYPE html>
<html>
 <head>
     <title>My Portfolio</title>
 </head>
 <body>
     <header>
         <h1>Welcome to My Portfolio</h1>
         <nav>
             <a href="#about">About</a>
             <a href="#projects">Projects</a>
             <a href="#contact">Contact</a>
         </nav>
     </header>
     <main>
         <section id="about">
             <h2>About Me</h2>
             <p>Hi, I'm a web developer with a passion for creating beautiful, functional websites.</p
         </section>
         <section id="projects">
             <h2>My Projects</h2>
             <article>
                 <h3>Project 1: E-commerce Site</h3>
                 <p>A responsive online store built with HTML, CSS, and JavaScript.</p>
             </article>
         </section>
         <footer>
             <p>&copy; 2025 My Portfolio</p>
         </footer>
     </main>
 </body>
</html>
```
//just put this into a .html

### Attributes
provide additional information about an element beyond default behavior.
exists as a name="value" pair.

Some Attributes I Didn't Know
- title: hover text
- target: specifies how link should be opened ("_blank" means new tab)

Best Practice
Always write descriptive and concise alt text for accessibility.
Avoid inline styling when possible, even for quick changes.
Use W3C HTML Validator to ensure  attribute use is appropriate.



# ==== Profile Page for Portfolio ====

CSS
separates how your content *looks* from how it is *organized*.
"cascading" refers to how CSS resolves conflicts between multiple **Style Rules**.
This is based on a hierarchy of importance and specificity.

Components
- the selector
 - the declaration block
  - properties
  - values
```
selector {
 property: value;
}
```
there is no need to memorize the countless properties.
practice and documentation will guide you as you learn.

Primary Selector Types
- Element `element`, `img`, `p`
- Class `.class`, `.profile-picture`
- Id `#id`, `#mainSearchBar`
//is this class and id casing representing best practice?

# Adding CSS

External
ideal method for applying consistent styles across multiple web pages.
added with `<link>` tag in `<head>` section
`<link>` Attributes
`<link rel="stylesheet" type="text/css" href="styles.css">`
- `rel="stylesheet"` specifies relationship between file and HTML (?)
- `type="text/css"` indicates type of file (CSS) (?)
- `href="styles.css"` file path

There is also Internal & Inline CSS. Will we learn the use cases later?
(Yes, in the next lesson!)



==== External, Internal, and Inline CSS ====
(Just continuing from last lesson, might reorganize these notes)

Internal
implemented between `<style>` tags.
- for single page projects/prototypes.
- for styles specific to one page.
- for short term disposable projects.

Inline
implemented within a tag using the `style` attribute.
`<p style="color: red;">this text is red</p>`
overrides External & Inline CSS
(Does it override the specific rule defined or all css rules?)
- quick fixes / testing small changes
- overriding existing styles for specific elements
- scenarios where editing external/internal CSS is not feasible.
  ie, when you're injecting HTML somewhere dynamically, or using a third party style sheet.

Specificity
determines which rules take precedence when multiple rules target an element.
specificity rank is based on the selector's type and placement (external/internal/inline)

Ranking (lowest to highest)
- Element Selectors `img`
- Class Selectors `.backpack-items`
- ID Selectors `#backpack`
- Inline Styles `style="color:red"`
*if two rules have the same specificity, the rule defined later in the code takes precedence ("cascades"?)

Specificity is first influenced by selector rules, then inline/internal/external placement, then it is the latest rule in that winning placement type.

Best Practices
- use External for multiple pages
- use Internal for single pages or prototypes
- reserve Inline for exceptional cases where overriding is necessary, or hacky quick fixes
- Avoid over-reliance on highly specific selectors. Too many ID's can be hard to maintain



# ==== HTML Forms ====

### What Is A Form?
*a collection of elements that collect and send input to a server*

The `<form>` Tag
- container of form's elements
- `action` attribute specifies URL data will be sent to. `action="/submit"` sends to /submit endpoint
- `method` attribute defines how data is sent.
 - `method="POST"` sends data in the "request body"(?). Used for sensitive/large data
 - `method="GET"` appends data to URL(what?). Used for simple queries/nonsensitive information.

Basic Structure
```
<form action="/submit" method="post">
   <label for="username">Username:</label>
   <input type="text" id="username" name="username">
   <input type="submit" value="Submit">
</form>
```



# Input Types

Text Input
- for single line responses
- `<input type="text" name="name" placeholder="Enter your full name">`
- `name` identifies the input when the form is submitted
- `placeholder` displays hint for what the input expects
- `required` (optional) ensuresd field must be filled before submission
- `id` important for JS targeting OR for a label to target

Submit Button
- sends the form data to server
- `<input type="submit" value="Submit">`
- `value` specifies the text displayed on the button.
- `disabled` (optional) prevents the button from being clicked.

Radio Buttons
- select *one* option from a group of options
- option set must be within `<fieldset>` tag
- individual options must be within `<label>` tags
- !!! `<legend>` tag must precede the options (?)
- `name` groups the options so only one can be selected. Each option must contain the same name.
- `value` defines data sent when radio button is selected
- `checked` (optional) pre-selects a button
```
<fieldset>
   <legend>Preferred Contact Method:</legend>
   <label for="email">
       <input type="radio" id="email" name="contact" value="email">
Email
   </label>
   <label for="phone">
       <input type="radio" id="phone" name="contact" value="phone">
Phone
   </label>
</fieldset>
```

Checkboxes
- select multiple options
- `input type="checkbox"`
- similar to radio buttons

Dropdown
- `select` tag container
- `option` tag options
```
<label for="country">Country:</label>
<select id="country" name="country">
   <option value="us">United States</option>
   <option value="ca">Canada</option>
   <option value="uk">United Kingdom</option>
</select>
```
- `selected` (optional) attribute preselects an option
- `multiple` (optional) allows multiple selections(?)

Textarea
- like text input, but with multiple lines.
```
<label for="message">Message:</label>
<textarea id="message" name="message" rows="5" cols="30" placeholder="Write your message here"></textarea>
```
- `rows` specifies number of visible lines
- `cols` specifies width of textarea in characters

Password
- hides user input with dots for privacy
```
<label for="password">Password:</label>
<input type="password" id="password" name="password" required>
```
- `maxLength` limits maximum number of characters

Email Input
- email inputs validate that the input matches a valid email format
```
<label for="email">Email:</label>
<input type="email" id="email" name="email" placeholder="example@example.com" required>
```


### Best Practice

Labels For Accessibility
- every input should have a corresponding `<label>` to describe its purpose
- these allow screen readers to convey the input's purpose to visually impaired users
- labels use the `for` attribute to link them to an element's `id`
`<label for="usernameInput">Username:</label>`

Fieldsets & Legends
- `<fieldset>` groups together related inputs, like checkboxes.
- `<legend>` provides a description for the group. (can legend be used elsewhere? what does legend mean?)

Clear Input Names
- the `name` attribute is the key in the submitted key-value pairs
- create "names" with this in mind

Miscellaneous
- use placeholder text for hints, but don't use it to describe data. It is less acessible and disappears when users start typing
- use `required` or `pattern` to enforce validaton before submission

Forms are confusing. I should reorganize these notes, practice with them, test with them, and research my own questions.

**Vim Notes**
I am taking these notes in vim for practice.
This is a cheat sheet for some important commands.
- ` h/j/k/l` arrow keys
- `:wq` save & quit
- `w/b` forwards & backwards
- `u/Ctrl+r` undo/redo
- `esc` exit insert mode
- `i` insert
- `a` append
- `o` append underneath
- `x` delete
- `dd` delete a line
https://vim.rtorr.com/ - cheat sheet

# ==== Java Data Types ====

Dynamically Typed Languages (JavaScript)
- variable types don't need outright defining
- a variable's type can change
```
let x = 5;
x = "Hello World!; //this is valid
```

Statically Typed Languages (Java)
- variable types are defined from the start
- variable types are unchangeable
```
String name = "John"
name = 5; //this is NOT valid
```


# Primitive Data Types
Whole Numbers
- byte:  up to 128 (Smallest unit of usable memory)
- short: up to 32,767 (2 bytes)
- int:   up to 2,147,483,647 (4 bytes)
- long:  up to 9,223,372,036,854,775,808 (8 bytes)

Decimal Numbers
- float: medium precision, less memory
- double: high precision, more memory

Other
- char: a text character
- boolean: true or false


# Object Data Types
- similar to JS' built in native classes
- includes state & sets of methods
- Java provides some, and you can build your own.
- use PascalCasing

String Data Type
- sequence of `char`s
- individual characters must be changed using methods, not accessed directly
```
String s = new String("Welcome!") //official way to create object data types.



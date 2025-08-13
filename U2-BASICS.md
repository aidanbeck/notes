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
String s = new String("Welcome!"); // official way to create object data types.
String myString = "Hello, World!"; // because strings are so common, there is the build in shortcut using string literals.
```
- doubles quotes "like this" are exclusively used for strings.
- single quotes 'l' are for single characters (chars)
- common String methods
 - charAt(x): returns chat at x index
 - substring(x,y): returns string of chars between x & y
 - length(): returns length
 - indexOf('a'): returns index of char 'a';
 - more: https://www.w3schools.com/java/java_ref_string.asp

**Array Data Type**
- an object data type, not a primitive
- fixed size
- all elements have the same type
`int[] arrayName = new int[5];`
- creates array of 5 ints
- the default value for an int in an array is 0
```
int literalNumbers = { 1, 2, 3, 4, 5 , 6, 7, 8, 9, 0 }
String[] students = { “Mike”, “Steve”, “Brian” }
```
- use curly braces to define the values of an array upon initialization
- this is called a "literal expression"

Accessing & Changing Elements
```
numbers[0] = 7;
int firstElement = numbers[0];
int arrayLength = numbers.length;
```

# Java Objects (Review)
- contain state (variables)
- contain behaviors (methods)
- `String` and `Array' are Java objects
- are not primitives



==== Building Java Applications in the Console ====

Writing To The Console
- `src/Main.java` is the program's starting point
- it defines a main class and main method, which is what gets run to call everything else
- System.out.println(""); is our console.log("");
```
public static void main(String[] args) {
 System.out.println("Hello World");
}
```

Reading From The Console
- the Scanner class is from the java.util package
- java.util is a built-in set of useful classes
- import with `import java.util.Scanner;`
- create scanner with `Scanner input = new Scanner(System.in);`
- this is our readline-sync, or prompt();
- scan with `input.nextLine();`, it stores the next line of input text
```
public static void main(String[] args) {
 Scanner scanner = new Scanner(System.in);
 System.out.print("Enter your name: "); //not println because it shouldn't end the line
 String name = scanner.nextLine();
 System.out.println("Hello, " + name + "!");
}
```
- there are other scanner methods for other data types, like .nextDouble() for doubles.


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
- `Shift` + `Insert` paste
:let &t_EI = "\e[2 q" | let &t_SI = "\e[2 q" | let &t_SR = "\e[2 q" - use block cursor.
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



==== Conditionals & Loops ====

#Conditionals

Mostly The Same
- if
- else
- else if

Switch & Case (Exists in JS but I need a review)
- for testing a value against multiple conditions
- more concise than exstensive if/else chains
```
switch (soupHeat) {
 case 1:
  //soup is cold
  break;
 case 2:
  //soup is warm
  break;
 case 3:
  //soup is hot
  break;
 default:
  //invalid soup temperature
}
```
- when a case is met, all cases underneath it will run until break; is hit
- this can be useful, but usually just remember to break; after each case.
- OR does it just do the cases that are also valid? I need to test this.
- maybe it can be used to do just if chains, and breaks are for stopping it.


# Loops

Mostly The Same
- while

Do While Loops
- similar to `while` loops.
- `while` loops check a condition, execute, & repeat
- `do while` loops execute *then* check the condition & repeat
- this means it will always execute at least once.
```
do {
 //execute code
} while (condition);
```

For Loops
- similar to JavaScript, but without `for of` and `for in`

For Each Loops
- iterate over elements of an array
```
for (String name : names) {
 System.out.println(name)
}
```
JavaScript Equivalent:
```
for (name of names) {
 console.log(name);
}
```

Break & Continue
- `break`: exit a loop
- `continue`: skip to the next iteration of the loop



==== Collection Data Types ====

Collection Data Types
- store several values within a single variable
- Arrays, ArrayLists, HashMaps, HashSets


# Arrays
- values of the same type
- each value is an "element"
- each element is at an "index"
- size explicitly defined, cannot be changed.
`int[] numbers = new int[5]`
- initialize array with the size
`int[] numbers = {0, 4, 5, 1};`
- initialize array with elements off the bat


# ArrayList
- can change size
- a Generic Type. includes a type parameter that specifies element type.
`ArrayList<String> names = new ArrayList<String>();`
- use `names.add("Alice");` to add elements, NOT `names[i]`
- remove with `names.remove(i)` or `names.remove("Bob");`
- (you can remove by index or value!)
- use `names.get(1)` to access elements.
- the for elements loop mentioned earlier also works.


# HashMaps
- store key-value pairs
- each key is unique
- like an JavaScript Object
- a Generic type. takes one parameter for the key type, and one for the value type.
`HashMap<String, Integer> ages = new HashMap<String, Integer>();`
- add key value pairs with `.put(key, value);`
- use it to update values too `.put(sameKey, differentValue);`
- `.put()` adds *and* updates key value pairs
- uses "hashing", it is faster to find values based on their keys
- like ArrayList, access values with `.get(key);`
- like ArrayList, remove pairs with `.remove(key);`

Iterate Over HashMaps
```
for (Map.Entry<String, Integer> entry : ages.entrySet()) {
 String name = entry.getKey();
 int age = entry.getValue();
 sout(name + " is " + age + " years old.");
}
```
- `.entrySet()` returns an iteratable "view" of the map?
- `.Entry` is a subclass of Map?
- `.getKey();` and `.getValue();` are methods of Entry?
- I need to research this more, but it seems the entrySet method and Entry subclass are ways of iterating over a hashmap.


# HashSets
- store unique elements
- cannot have duplicates
- if you try to add an existing element, there is no effect
- like a HashMap, but the key *is* the value
- Generic Type
- has a `.contains()` method.

Declaring & Initializing
`HashSet<String> names = new HashSet<String>();`
- can they be types other than Strings?

Methods
```
names.add("Alice"); // adds "Alice"
names.add("Bob");   // adds "Bob"
names.add("Alice"); // duplicate, so nothing happens.
names.remove("Bob");// removes "Bob"

names.contains("Alice"); // returns true
names.contains("Bob");   // returns false
```
- add with `.add();`
- remove with `.remove();`
- detect existence with `.contains();`

Iterate
```
for (String name : names) {
 System.out.println(name);
}
```
- You can iterate the normal way.

note: HashMap and HashSet values are not stored in any particular order.
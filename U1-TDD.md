
==== Test Driven Development In Jest====

**Unit Testing**
*Unit Testing* allows you to verify a method produces the correct output over a set of inputs. We will use the testing framework *Jest*.
- Identify methods to test.
- Write clear test cases.
- Run them to validate behavior.

This not only prevents bugs, but allows you to carefully consider the intention of a function. It also takes guesswork out of manual testing, you have proof it works. Additionally, it eliminates "Regression", or when adding a feature breaks another feature without being noticed. Finally, they work as documentation, showing how a function can be used and how it works without the need to think through the code itself. Unlike normal documentation, tests will always be updated if testing is a part of the process.

**Jest**
*a unit testing JavaScript framework.*
- make a folder like "tests" where all test files are to be stored.
- make test files with the .test.js extension. tests for hello.js will be in tests/hello.test.js
- "**package.json**: Jest is listed under devDependencies or dependencies in this file"
- optionally, there is a jest.config.js file.

Jest Methods:
- describe: Groups related tests into a test suite.
- test: Defines individual test cases.
- expect: States the expected result.
- toBe: Compares the actual and expected values.

*Then, run tests in terminal with "npm test".*

Example
```
const hello = require('../hello.js');

describe("hello", function(){
    test("should return a custom message name when name is specified",
    function() {
        expect(hello("Jest").toBe("Hello, Jest!");
    });
    
    test("should return a general greeting when name is not specified",
    function() {
        expect(hello()).toBe("Hello, World!");
    });
});
```

Types of Test Cases
- Positive: verify expected behavior with valid inputs
- Negative: check behavior with invalid inputs
- Edge: test inputs at the extreme boundaries of valid inputs

Example of Case Types
*imagine a function that accepts numbers between 50 and 160*
- Positive: 56, 75, 80
- Negative: -1, 161, "70"
- Edge: 50, 160



==== The Test/Code Cycle: Red, Green, Refactor ====
[[#]] The Complete JavasScript Course #

- GitHub: https://github.com/jonasschmedtmann/complete-javascript-course
- Resources: http://codingheroes.io/resources/
- This file: https://bitbucket.org/jonwhittlestone/learning-complete-js-course/src/master/readme.md

### Style

- Airbnb JS style guide: https://github.com/airbnb/javascript
- JavaScript is almost pythonic: https://dev.to/massa142/javascript-is-almost-pythonic-3f8

---

## 02 - Language Basics

### 2/008/160 Variables/Data Types

- undefined is a primitive data type given to unassigned variables
- variables can start with an underscore or a dollar sign (and a letter)

### 2/009/160 Variable Mutation and type coercion

- JavaScript automatically converts types from one to another as needed eg. booleans will get converted/coerced into a string
- Declare variables on the same line

### 2/010/160 Maths Operators

- typeof operator

### 2/011/160 Operator precedence

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence
- associativity (assignment works from right to left)

- `x = x * 2`
  is the same as
  `x *= 2`

### 2/012/160 Coding Challenge

### 2/013/160 Solution

### 2/014/160 If/Else

### 2/015/160 Boolean Logic

- `else if` block
  `- AND`
- truth tables

### 2/016/160 Ternary operator

- Write if/else statement in one line
- called ternary bc it has 3 operands

  `age >=18 ? console.log('drinks beer') : console.log('drinks juice');`

- switch statement / multiple case clauses
  ```
  switch (true) {
      // trick to make switch statement function as if/else
  }
  ```

````
### 2/017/160 Truthy and Falsy values  ###
- falsy values: undefined, mull, 0, '', NaN
- declared a variable with `var height` but didn't define it
- triple === where as double `==` does type coercion so type doesn't have to match ie. `23 == '23' = true`

### 2/018/160  Coding Challenge 2 ##

### 2/019/160  Coding Challenge 2 solution ##

### 2/020/160  Functions ##
- functions important for DRY principle
- `yearsUntilRetirement(year, firstName)`

### 2/021/160  Function expressions and function declaration ##
- function statement is where you assign a function to a variable
- expression is always when it results in a single value
- a statement (if/else etc) doesn't produce immediate value
- global concept

### 2/022/160  arrays ##
- declare with `var names = []` or `var years = new Array()`
- `names.length`
- can be different data types
- `names.push(4)` adds to the end of the array
- `names.unshift('Mr')` adds to the beginning
- `names.pop()` removes element from the end
- `names.shift()` removes the element from the beginning
- `names.indexOf(1990)` will return position of 1990  (if not present will return -1)

### 2/023/160  coding challenge - tip calculator  ##

### 2/024/160  coding challenge solution - tip calculator  ##

### 2/025/160  Objects and properties ##
- object literal: container we can fill with properties (key/value pairs)
- can use variable string for a key to an object `john[x]`


### 2/026/160  Objects and methods ##
- function expression in an object
- from within an object, we can access a property of the object with `this` to refer to the current object
- we can set properties dynamically


### 2/027/160 Coding Challenge object creation ###

### 2/028/160 Coding challenge solution  ###

### 2/029/160 Loops and iteration  ###

### 2/030/160 Coding Challenge  ###

### 2/031/160 Coding Challenge solution  ###
- member operator precendence `this.bills.length`

### 2/032/160 Coding Challenge solution  ###

### 2/033/160 JavaScript versions ES2015 and ES6+  ###
- ECMAScript to refer to the standard
- ES6 released in 2015. ES2015 is the official name but changed to an annual release cycle: ES7/ES2016, ES8/ES2018
- Best to learn fundamentals (ES5)

----
## 03 - How Javascript works behind the scenes ##

### 3/034/160 Get started section 3  ###

### 3/036/160 JS behind the scenes  ###

### 3/037/160 Execution context  ###
- the order in which the code is run
- `lastName` is a property of the window object
- `lastName === window.lastName`
- Global Execution Conext is code that is not inside of any function
- variables inside a function get their own execution context. This gets put on top of the global execution conext on the execution stack
- active context  but when function returns, the context is popped off the stack

### 3/038/160 How do execution contexts get created / why are they imp  ###
- all the functions are stored in the variable object, even before the code starts executing
- hoisting: code is scanned for variable declarations and each property is created in the Variable Object and set to undefined
- Functions and Variables are hoisted which means they are available before execution begins.


### 3/039/160 Hoisting in practice  ###
- functions are available in the variable object
- Function expressions can't be used before declaration (Hoisting only works for function delcarations)

### 3/040/160 Scoping Chain  ###
- Lexical scoping means the child function will also have access to its parent scope
- only if JavaScript does not find the variable anywhere on the scope chain does it throw an error

### 3/041/160 `this` keyword  ###
- last step of the creation phase of execution context object- determining value of `this` keyword
- in a method call the `this` keyword points to the object that is calling the method
    - not assigned a value until a function where it's defined is called

### 3/042/160 `this` keyword  ###
- when used in a regular function call and not a method (inside an object), `this` refers to the window object which is a global object
- When a regular function call happens (even inside a method), the default object is the Window object
- Can reassign one method from an object to another
    ```
    mike.calculateAge = john.calculateAge;
    ```

----
## 04 JavaScript in the Browser: DOM Manipulation and Events ##
- How to create our fundamental game variables
- How to generate a random number
- How to manipulate the DOM
- How to read from the DOM
- How to change CSS styles

- Set up Event handler          (lecture 49)
- What a callback function is   (lecture 49)
- What an anonymous function is (lecture 49)
- Another way to select items by ID (lecture 49)
- How to change image in an `<img>` element (lecture 49)

### 4/043/160 intro ###

### 4/045/160   The DOM and DOM Manipulation ###
- DOM is a structured representation of an HTML document

### 4/046/160   HTML/CSS  ###

### 4/047/160   Project Setup & Details  ###

### 4/048/160 DOM Access/Manipulation ###
- `Math.floor()     // removes the decimal point of a number`
- Generating a random rolled dice number

    ```Math.floor(
        (Math.random() * 6) + 1
    )```
 - `document.querySelector('#score + currentPlayer').innerHTML = dice  // set DOM contents as HTML of dice for current player (because of type coercion`)
    - https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector
- `document.querySelector('dice').style.display = 'none'    // hide an element`

### 4/049/160 Display value each time we click with Events and Event Handling  ###
- Events are input that notify code that something has happened
- Event listener is a function that waits for a specific event to happen
- An event can only be processed as soon as the execution stack is empty (all functions have returned)
- There is a message queue where all events are waiting to be processed (but only happens once execution stack is empty - Global Execution stack)
- `document.querySelector('.btn-roll').addEventListener('click', btn);`
    - https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener
- an anonymous function doesn't have a name and can't be reused

### 4/050/160 Updating scores  ###
- modifying the html class with code to change elements visual appearance
    - As soon as the player changes
        - `document.querySelector('.player-0-panel').classList.toggle('active')`

### 4/051/160 Hold function and DRY (Don't repeat yourself) principle  ###

### 4/052/160 Initilisation  ###
- `init()` function
- pass into the event listener function


### 4/053/160 State Variable  ###
- tells us the conduition of a system ie. is the game playing, or not playing

### 4/054/160 Coding Challenge 6 ###

### 4/055/160 Coding Challenge 6 ###

### 4/057/160 Coding Challenge Solutions ###
- the condition for the two 6s must be before the condition for the 1
- we don't want the users to be able to enter/use an empty value for the score target

----
## 05 Advanced Javascript Functions and Objects ##

### 5/058/160 New Section, Objects and Functions ###

### 5/059/160 Objects/Prototypes ###
- based on a constructor, you can create as many instances of any object as you like
- every object has an prototype property which makes inheritance possible in JS
    - add that method to the persons prototype property if you want it to be inherited
    - so other derived objects will inherit, add to the prototype of the object
    - the `Object` object is the parent of every object that is created in js
- The prototype chain describes {instance} > {Class} > `Object`
- the final link in the prototype chain is `null` and has no prototype


### 5/61/160 Creating objects ###
- function constructor is a pattern for writing a blueprint
    ```
        var Person = function(name, yearOfBirth, job) {
            this.name = name;
            this.yearOfBirth = yearOfBirth;
            this.job = job;
        }
        Person.prototype.calculateAge = function () {
            console.log(2016 - this.yearOfBirth);
        }
        var john = new Person('John', 1990, 'teacher'); // instantiaton
        john.calculateAge();    // is an inherited method
    ```
-  move the method to the function to the prototype property of function constructor from the constructor

### 5/62/160 Prototype chain in console ###
- `john.__proto__ === Person.prototype              // true`
- `john.__proto__.__proto__ === Object.prototype    // true`
- like you can do `john.hasOwnProperty('job');      // true`
- but an inherited property will give false
- Alsmost everything is an object, apart from int, null, String
- `console.info(x);     // look inside of an object`
- can see `x.__prototype__      // the array function constructor`

### 5/63/160 Creating objects that inherit from a prototype ###
- using prototype as arguement to `create()` function
    ```
        var personProto = {
            calculateAge: function() {
                console.log(2016 - this.yearOfBirth);
            }
        };

        var jane = Object.create(personProto, {
            name: { value: 'Jane' },
            yearOfBirth: { value: 1969 },
            job: { value: 'designer' }
        });
    ```

### 5/64/160 Primitives vs. Objects ###
- Numbers, Strings, Booleans, Undefined, Null are primitives
- Everything else are objects
- Primitives are where data is actually stored in data itself (but a copy) whereas objects contain a reference in memory to where the object is stored
- when passing into a function, when logging out the values after, the primitive value remains unchanged after a mutation (as a simple copy is created), but the object (reference) is changed

### 5/65/160 First class functions  ###
- remember, fuctions are also objects
- remember, we can pass functions as an arguement to another function

- first class functions are where we return a function from a function
- writing functions as arguements (callback functions)
- when initially passing the callback function, we don't add parens as we don't want it called. It's a 'callback' function as it's called later
    ```
        var ages = arrayCalc(years, calculateAge);
    ```
- can pass multiple functions as callbacks into the generic function that loops over the ages array `arrayCalc()` and so it's more reuseable, modular and readable

### 5/66/160 functions returning functions - a higher order function  ###
- an anonymous function doesn't have a name
- a higher order function
- Another technique is to call outer function straight away and then pass into it the argument so it immediately invokes
    ```
        interviewQuestion('teacher')('mark');       // inteviewQuestion() returns a function that interpolates 'mark' into it
    ```
- it works because it is evaluated from left to right
-
### 5/67/160 immiediately invoked function expressions - IIFE  ###
- https://developer.mozilla.org/en-US/docs/Glossary/IIFE
- Create a new scope that is hidden from the outside scope where we can safely put variable and don't intefere with outher variables in our global execution context
- javascript function that runs as soon as it's defined
- write an anonymous function within parentheses, and then invoke it
- we need to trick the parser into thinking we present the function as a experssion not a declaration because in JS, what's inside a parens cannot be  astatement
- it would neve do anything if we didn't add the parens at the end
````

    // NOT GREAT because we don't want to access score variable from outside
    function game() {
        var score = Math.random() * 10;
        console.log(score >= 5);
    }
    game();

    // BETTER because it ensures data privacy, we can't `console.log(score)'
    (function () {
        var score = Math.random() * 10;
        console.log(score >= 5);
    })();

````

### 5/68/160 Closures  ###
- A feature that is built-in to JS
- Where an anonymous function is returned from a function, it still has access to the outer functions variables and args despite the outer function has already stopped its execution (has already returned)
- The variable object of the outer function is still there, the scope chain stays in tact so we can access variables of the outer function long after it has completed exection
- the current execution context has closed in on the outer variable object so it can used it so the scope chain always stays in tact


### 5/69/160 Bind, Call and Apply methods  ###
- method borrowing: using the `call()` method to allow one object to use the method of another
-
    ```
        john.presentation(emily, 'friendly', 'afternoon');      // emily is the 'this' variable/another object, and then pass into it the arguments that are needed
    ```
-  similarly `john.presentation.apply(emily,['friendly', 'afternoon']);     // arg list as an array`
- `bind()` method allows us to create a function with preset arguments, so we can create copies with a default. It can be called again later without specifying the default arg
- currying is where we create fuction based on another function with some preset already defined

### 5/70/160 Coding challenge 7 ###
- See `./jw/070-challenge-7/index.html`

### 5/71/160 Coding solution 7 ###
### 5/72/160 Coding solution 7 ###
----
## 06 Putting it all together in Budget App ##

### 6/73/160 Budget App ###

### 6/75/160 Budget App Project Details ###

### 6/76/160 Plan/Architecture ###
- identify the fundamental things as a todo list so you can arrange items into modules
- structure code with modules into logical parts to keep organized but also to encapsulate data for privacy (and also expose data publicly)

### 6/77/160 Module pattern ###
- public/private data, encapsulation, separation of concerns
- private variables/methods and public variables/methods
- only expose a public interface / sometimes called an API
    [[-]] to expose a public interface we must know concepts of closures and IIFE (an anonymous function wrapped in parens)
    - from the IIFE, return an object containing all functions we wish to be public
- module pattern allows for separation of concerns, presentation in one module, data in another

### 6/78/160 Set up Event listener ###
- Event object
- pass the `Event` argument into the callback for `addEventListener()`
    - `KeyboardEvent` has a prototype of `UIEvent` which has a prototype which is an `Event` etc
    - use to determine `keyCode`

### 6/79/160 Reading input data ###
- write a public method in UIController and call it from other controller
- how to return 3 variables at the same time? return an object with properties

### 6/80/160 Better structure: init function ###
- make it so we only have functions in the controller `controller.setupEventListeners()`
- call `setupEventListners()` from `init()`

### 6/81/160 storing data in budgetController / function constructors  ###
- function constructors start with a capital letter
- add prototypes so that each object will inherit the method rather than being added to each individual object
    - why function constructors work - the `new` keyword creates an empty object and calls the Expense function and points the `this` keyword of that function to the new object that was created
-


----
## 07 Next generations JavaScript: Intro to ES6 / ES2015

X/123/160 Promises ?


more stuff
----
## 08 Loading from an API / Babel / React / Webpack

stuff
````

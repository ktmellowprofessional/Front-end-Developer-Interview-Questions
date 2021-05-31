---
title: JavaScript Questions
layout: layouts/page.njk
permalink: /questions/javascript-questions/index.html
---
answers from repo contributor: https://frontendinterviewhandbook.com/en/javascript-questions/#explain-the-difference-between-mutable-and-immutable-objects
answers2: https://codeburst.io/clearing-your-front-end-job-interview-javascript-d5ec896adda4
answers3: https://medium.com/@nupoor_neha/javascript-front-end-interview-questions-1cbc5e32792b#:~:text=What%20language%20constructions%20do%20you,in%2C%20map%2C%20reduce%20etc.

* Explain event delegation.
  Event delegation is a technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant elements due to event bubbling up the DOM. The benefits of this technique are:
  Memory footprint goes down because only one single handler is needed on the parent element, rather than having to attach event handlers on each descendant.
  There is no need to unbind the handler from elements that are removed and to bind the event for new elements.

* Explain how `this` works in JavaScript.
  * Can you give an example of one of the ways that working with `this` has changed in ES6?
  This is the current context. 
  It can refer to global context in an invoked function.
  In the strict mode, JavaScript sets the this to undefined.
  It can be the new object in a class context.
  If this is called within a function with new (instance call) then this refers to new object instead of global this or use strict undefined.
  If function is called with bind/call/apply, then this is the passed object.
  https://www.javascripttutorial.net/javascript-this/

* Explain how prototypal inheritance works.
  All JavaScript objects have a prototype property, that is a reference to another object. When a property is accessed on an object and if the property is not found on that object, the JavaScript engine looks at the object's prototype. and the prototype's prototype and so on, until it finds the property defined on one of the prototypes or until it reaches the end of the prototype chain. This linear behaviour simulates classical inheritance, but it is really more of delegation than inheritance.

* What's the difference between a variable that is: `null`, `undefined` or undeclared?
  Null can be assigned to a variable to represent no value. It is an assignment value.
  Undefined property indicates that a variable has not been assigned a value, or not declared at all.
  An undeclared variable (foo = 4 instead of var foo = 4) makes it global scope

* How would you go about checking for any of these states?
  Check typeof
  undefined is "undefined"
  null is "object"

* What is a closure, and how/why would you use one?
  Closures are inner functions inside of an outer function. They have their own local scope and has access to outer function’s scope, parameters (but NOT arguments object), and they also have access to global variables.

  From what I understand, Closures is a neat way to deal with scope issues. Reasons we use Closures is because Javascript is a function-level scope rather than as with other languages, block-level scope and Javascript is an asynchronous/event driven language. Example that Closure is frequently used is jQuery (ex. click()).

  a = (function () {
    var privatefunction = function () {
        alert('hello');
    }

    return {
        publicfunction : function () {
            privatefunction();
        }
    }
  })();
  Prevent access to privateFunction but allow access to public function by calling function a.

* What language constructions do you use for iterating over object properties and array items?
  array prototype functions
  for loop
  for... in
  for... each

* Can you describe the main difference between the `Array.forEach()` loop and `Array.map()` methods and why you would pick one versus the other?
* What's a typical use case for anonymous functions?
* What's the difference between host objects and native objects?

* Explain the difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
class definition
  assigning the class definition (/function def) to a variable
  assigning person the outcome return value of Person function if any
  initiating an instanced object of a class 

* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
  function foo(){} is an declaration and is hoisted. 
  var foo = function() {} is an expression with an anonymous function.

* Can you explain what `Function.call` and `Function.apply` do? What's the notable difference between the two?
  Invokes a function with context object reassignment (this)
  Call takes args one at a time comma sep
  Apply takes args as array

* Explain `Function.prototype.bind`. 
  Returns method with different context object (this) passed in

* What's the difference between feature detection, feature inference, and using the UA string?
  feature detect:
  if (navigator.geolocation) {
  // detect users location here B-) and do something awesome
  }
  or
  if('localStorage' in window)
  This is more specific way and best practice to check if a feature exists

  feature inference is bad practice because it assumes based on one feature existing that the rest exist.
  
  UA string:
  navigator.userAgent 
  UA is useragent and this method shouldn't be used because it doesn't help with features dependent on UA version

* Explain "hoisting".
  Variable hoisting means the JavaScript engine moves the variable declarations to the top of the script.
  JavaScript only hoists declarations, not initializations (the value of vars are not brought to top, only the var name).
  Function declarations function foo(){} are hoisted.

  This happens with function declarations, but not with function expressions or arrow functions.
  // Example 1
    // Only y is hoisted

    x = 1; // Initialize x, and if not already declared, declare it - but no hoisting as there is no var in the statement.
    console.log(x + " " + y); // '1 undefined'
    // This prints value of y as undefined as JavaScript only hoists declarations
    var y = 2; // Declare and Initialize y

    // Example 2
    // No hoisting, but since initialization also causes declaration (if not already declared), variables are available.

    a = 'Cran'; // Initialize a
    b = 'berry'; // Initialize b

    console.log(a + "" + b); // 'Cranberry'

* Describe event bubbling and event capturing.
  Event Bubbling − Whenever an event happens on an element, the event handlers will first run on it and then on its parent and finally all the way up to its other ancestors. Event Capturing − It is the reverse of the event bubbling and here the event starts from the parent element and then to its child element.

  So two click handlers assigned to parent and child... parent would trigger first.
  However, we would use event bubbling / propagation to delegate event handling so we don't have to put a handler on every single child. 

* What's the difference between an "attribute" and a "property"?
  Attributes come from markup in the browser html.
  Properties are part of the element's object.
  Most of the time, its better to work with properties. Their values and names tend to be consistent across browsers. We’ll only work with attributes when there is no properties set, example is custom attributes data-*.

* What are the pros and cons of extending built-in JavaScript objects?
  Extending a built-in/native JavaScript object means adding properties/functions to its prototype. While this may seem like a good idea at first, it is dangerous in practice. Imagine your code uses a few libraries that both extend the Array.prototype by adding the same contains method, the implementations will overwrite each other and your code will break if the behavior of these two methods is not the same.

  The only time you may want to extend a native object is when you want to create a polyfill, essentially providing your own implementation for a method that is part of the JavaScript specification but might not exist in the user's browser due to it being an older browser. Accessible everywhere.

* What is the difference between `==` and `===`?
  Loose typing vs strict typing
  Strict typing is better

* Explain the same-origin policy with regards to JavaScript.
  The same origin policy states that a web browser permits script contained in one page (or frame) to access data in another page (or frame) only if both the pages have the same origin. It is a critical security mechanism for isolating potentially malicious documents. Two pages have the same origin if the protocol, port (if one is specified), and host are the same for both pages. Read details here and here.
  If you see Cross Origin Resource Sharing errors, it is because the server host side must set Access Control headers to allow the recipient to use that asset.
  Origin can be checked with location.origin (e.g. https://www.google.com)
  Usually the base site/domain

* Why is it called a Ternary operator, what does the word "Ternary" indicate? 
  3 operands (3 math operation arguments)

* What is strict mode? What are some of the advantages/disadvantages of using it?
  Eliminates some JavaScript silent errors by changing them to throw errors.
  Fixes mistakes that make it difficult for JavaScript engines to perform optimizations: strict mode code can sometimes be made to run faster than identical code that's not strict mode.
  Prohibits some syntax likely to be defined in future versions of ECMAScript.

  Main purpose of using strict mode is to be able to evaluate your JavaScript code and throw more errors in an effort to make your code more robust, readable, accurate and fixes compatibility issues that may arise for future JavaScript releases.

  Prevents silent errors, compatibility issues, and prevents bad practices like using global object.

* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
  Advantages:
  Fixes some of the longstanding problems in JavaScript and discourages JavaScript anti-patterns.
  Enables you to write shorter code, by providing some syntactic sugar on top of JavaScript, which I think ES5 lacks, but ES2015 is awesome.
  More helpful dev features

  Disadvantages:
  Require a build/compile process as browsers only run JavaScript and your code will need to be compiled into JavaScript before being served to browsers.
  Debugging can be a pain if your source maps do not map nicely to your pre-compiled source.
  Most developers are not familiar with these languages and will need to learn it. There's a ramp up cost involved for your team if you use it for your projects.
  Smaller community (depends on the language), which means resources, tutorials, libraries, and tooling would be harder to find.
  IDE/editor support might be lacking.
  These languages will always be behind the latest JavaScript standard.
  Developers should be cognizant of what their code is being compiled to — because that is what would actually be running, and that is what matters in the end.

* What tools and techniques do you use debugging JavaScript code?
  breakpoints, debugger, console log, unit tests, mocking, tdd

* Explain the difference between mutable and immutable objects.
  Immutability is a core principle in functional programming, and has lots to offer to object-oriented programs as well. A mutable object is an object whose state can be modified after it is created. An immutable object is an object whose state cannot be modified after it is created.
  In JavaScript, some built-in types (numbers, strings) are immutable, but custom objects are generally mutable.

  * What is an example of an immutable object in JavaScript?
    Some built-in immutable JavaScript objects are Math, Date
    Use Object.assign() to create a differing object
    Object.freeze() prevent mutating the first layer but not nested layers
    Object.preventExtensions()

  * What are the pros and cons of immutability?
    pros:
    It makes certain features easier
    Your data changes are more explicit
    Easier to detect object changes by detecting new object memory location

    cons:
    It is less performant than mutable approach with small datasets

  * How can you achieve immutability in your own code?
    Use Object.assign() to create a differing object
    Object.freeze() prevent mutating the first layer but not nested layers
    Object.preventExtensions()
    libraries

* Explain the difference between synchronous and asynchronous functions.
  Synchronous functions are blocking while asynchronous functions are not. In synchronous functions, statements complete before the next statement is run. In this case, the program is evaluated exactly in order of the statements and execution of the program is paused if one of the statements take a very long time.

  Asynchronous functions usually accept a callback as a parameter and execution continue on the next line immediately after the asynchronous function is invoked. The callback is only invoked when the asynchronous operation is complete and the call stack is empty. Heavy duty operations such as loading data from a web server or querying a database should be done asynchronously so that the main thread can continue executing other operations instead of blocking until that long operation to complete (in the case of browsers, the UI will freeze).
* What is event loop?
  Answer 1:
  The event loop is a single-threaded loop that monitors the call stack and checks if there is any work to be done in the task queue. If the call stack is empty and there are callback functions in the task queue, a function is dequeued and pushed onto the call stack to be executed.

  * What is the difference between call stack and task queue?
  Call stack is LIFO 
  Task queue is FIFO

* What are the differences between variables created using `let`, `var` or `const`?
  const prevents reassignment/redeclaration and is block scoped
  let expects reassignment but prevents redeclaration and is block scoped
  var allows anything and is function/globally scoped

* What are the differences between ES6 class and ES5 function constructors?
  https://frontendinterviewhandbook.com/en/javascript-questions/#what-are-the-differences-between-es6-class-and-es5-function-constructors
  Under the hood, they are the same. ES6 is syntactic inheritance. It makes it easier to read/write inheritance since you don't have to write 2 blocks for function declaration and prototype assignment.

    // ES5 Function Constructor
    function Student(name, studentId) {
      // Call constructor of superclass to initialize superclass-derived members.
      Person.call(this, name);

        // Initialize subclass's own members.
        this.studentId = studentId;
      }

      Student.prototype = Object.create(Person.prototype);
      Student.prototype.constructor = Student;

    // ES6 Class
    class Student extends Person {
      constructor(name, studentId) {
        super(name);  // super is analagous to doing Parent.call(this, propertyName)
        this.studentId = studentId;
      }
    }

* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
  Binds the context of where it is defined. (lexically bound)
  this value inside a regular function is dynamic and depends on the invocation.
  If the arrow function has one expression, then the expression is returned implicitly, even without using the return keyword; You can define methods using the arrow function syntax inside classes. Fat arrow methods bind this value to the class instance.

* What advantage is there for using the arrow syntax for a method in a constructor?
  Fat arrow methods bind this value to the class instance.

* What is the definition of a higher-order function?
  Takes a function as an argument and returns a function

* Can you give an example for destructuring an object or an array?
  Destructuring is making a single var into multiple vars.
  const [b, c, ...more] = ['alpha', 'beta', 'gamma', 'delta', 'epsilon'];
  const { pumpkin, pieCrust, spice} = pieIngredients;

* Can you give an example of generating a string with ES6 Template Literals?
  const name = "Katie"
  const myStr = `My name is ${name}.`

* Can you give an example of a curry function and why this syntax offers an advantage?
  Curry functions are neat when used to carry containers of reusable code. Basically you take a function with multiple arguments and you know that one of those arguments will have specific value but the other is undecided. Therefor by using curry, as a fancy partial application, you can create a new function which will allow you to deal only with the undecided arguments without repeating your code.

* What are the benefits of using `spread syntax` and how is it different from `rest syntax`? 
  Spread is all, rest is the rest.
  ( ...all ) => {}
  ( first, second, ...rest ) => {}

* How can you share code between files?
  Use es6 import module
  Use es5 require module

* Why you might want to create static class members?

* What is the difference between `while` and `do-while` loops in JavaScript?
  Do-while executes loop at least once.

* What is a promise? Where and how would you use promise?
  A function that takes resolve and reject and can be in pending state until success/failure criterion are met, which puts it in resolved state. 
  When you want to wait for a result before invoking the callback. Can specify certain callbacks for success/fail.

## Coding questions
* Write an immediately invoked function expression (IIFE)
  (function foo(){ }())
# JavaScript

## JavaScript

JavaScript is a high-level, interpreted programming language.

## ES6 New Features

* Let, Const
* Class
* Arrow Function
* Spread and Destructing
* Modules
* Promise
* Symbol

## How JavaScript work

![](https://github.com/yao2007/study-node/tree/3c6d34232e6101eff8213fdac978957736ea079c/.gitbook/assets/image%20%2811%29.png)

## Shallow Comparison Check

The shallow comparison check means that JavaScript only checks that the value's object IDs are the same, not their contents are the same. The ID here means the memory address for where JavaScript stores the information for that particular object.

## Hoisting

Hoisting is a term used to explain the behavior of variable declarations in your code. Variables declared or initialized with the `var` keyword will have their declaration "moved" up to the top of the current scope.

However, only the variable declarations and function declarations are hoisted. Variable assignments and function expressions are not hoisted.

## Closure

A closure is an inner function that has access to the variables in the outer \(enclosing\) function's scope chain. Closure is a function that returns a function. It gives the access to an outer function's scope from an inner function. To use the closure, simply define a function inside another function and return it or pass it to another function.

The closure has access to variables in three scopes

* variables in its own scope
* variables in the enclosing function's scope
* global variables

We can use Closure to declare a private variable.

## Higher-Order Function

A higher-order function is any function that takes one or more functions as arguments, which it uses to operate on some data, and/or returns a function as a result. Higher-order functions are meant to abstract some operation that is performed repeatedly. e.g.`map`, `forEach`, `filter`, `reduce`, `bind`.

## Currying

Currying is a pattern where a function with more than one parameter is broken into multiple functions that, when called in series, will accumulate all of the required parameters one at a time. This technique can be useful for making code written in functional style easier to read and compose. It's important to node that for a function be curried, it needs to start out as one function, then broken out into a sequence of functions that each accepts one parameter.

## `this` in JavaScript

The value of `this` depends on how the function is called.

The following rules are applied:

* If the `new` keyword is used when calling the function, `this` inside the function is a brand new object.
* If `apply`, `call` or `bind` are used to call/create a function, `this` inside the function is the object that is passed in as the argument. 
* If a function is called as a method, such as `obj.method()`, `this` here is the object that the function is a property of. 
* If a function is invoked as a free function invocation. meaning it was invoked without any of the conditions present above, `this` is the global object. In a browser, it is the `window` object. If in strict mode \(`"use strict"`\), `this` will be `undefined` instead of the global object. 
* If multiple of the above rules apply, the rule that is higher wins and will set the `this` value.
* If the function is an ES6 arrow function, it ignores all the rules above and receives the `this` value of its surrounding scope at the time it is created. 

## Window vs Document

`window` is the main JavaScript object root, like the global object in the browser, also can be treated as the root of the DOM.

`document` is the main object of the rendered DOM.

## Falsey Values

* 0
* null
* undefined
* ""
* false
* NaN

## 4 types of Scoping

* Global Scope - declared outside for any function, use it without declaring
* Function Scope - `var`
* Block Scope - `let & const` 
  * `const`: immutable variable, must be initialized
* Module Scope

## Prototypal Inheritance

All JavaScript objects have a prototype property, that is a reference to another object. When a property is accessed on an object and if the property is not found on that object, the JavaScript engine looks at the object's prototype, and the prototype's prototype and so on, until it finds the property defined on one of the prototypes or until it reaches the end of the prototype chain. This behavior simulates classical inheritance, but it is really more of delegation than inheritance.

## Classical inheritance vs Prototypal inheritance

classical inheritance: a description of the object to be created. Classes inherit from classes and create subclass relationships.

prototypal inheritance: a prototype is a working object instance. Objects inherit directly from other objects.

## `null` vs `undefined`

A variable that is `undefined` is a a variable that has been declared, but not assigned a value. It is of type `undefined`.

A variable that is `null` will have been explicitly assigned to the `null` value. It represents no value and is different from `undefined` in the sense that it has been explicitly assigned. It is of type `object`.

`undefined == null // true`

## Create an Object in 6 different ways

* Object\(\) constructor 

```javascript
const obj = new Object();
```

* Object.create\(\) 
  * creates a new object extending the prototype object passed as a parameter 

```javascript
const obj = Object.create(null);
```

* Bracket's syntactic sugar
  * equals to Object.create\(null\), using a null prototype as an argument

```javascript
const obj = {};
```

* Function constructor 
  * call a function and setting this of the function to a fresh new Object, and binding the prototype of that new Object to the function's prototype

```javascript
const obj = function(name) {
    this.name = name
};        
const a = new obj("hello");
```

* Function constructor + prototype

```javascript
function myObject() {};
myObject.prototype.name = "hello";
const obj = new myObject();
```

* ES6 class syntax 

```javascript
class myObject {
    constructor(name) {
        this.name = name;
    }
}
const obj = new myObject("hello");
```

* Singleton pattern 

```javascript
 const obj = new function() {this.name = "hello"};
```

## Promise

* Promise represents the eventual completion of an async operation
* It must be in one of these states
  * pending
    * initial state, not fulfilled or rejected
  * fulfilled
    * meaning that the operation completed successfully
  * rejected
    * meaning that the operation failed
* It is guaranteed that a promise object will either succeed or fail
* promise.all 
  * returns a single promise that resolves when all of the promises in the argument have resolved or when the utterable argument contains no promises
* create Promise example

```javascript
function asyncDoubble(n) {
    return new Promise((resolve, reject) => {
        if (typeof n === "number") {
            resolve(n * 2);
        } else {
            reject(new Error (n + "is not a number!"));
        }
    });
}
asyncDouble(3).then(
    data => console.log(data);
    error => console.log(error);
);
```

## Callback Function

A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action. e.g. addEventListener

## Callback Hell

Callback Hell is referred to the problems caused by asynchronous AJAX calls, which means where are multiple nested callbacks.

### How to fix:

* keep the code shallow
* modularize
* handle every single error

## How to make HTTP request

* AJAX
* jQuery 
* Fetch
* Axios

## Fetch

A Fetch API provides a fetch method defined on a window object, which you can use to perform requests and sent it to the server. This method returns a Promise that you can use to retrieve the response of the request.

## Null process

A null process - which takes its name from the concept of null pointers - is what happens when no formal process is put in place

## BFS vs DFS

| BFS | DFS |
| :--- | :--- |
| BFS visit nodes level by level in Graph | DFS visit nodes of graph depth wise. It visits nodes until reach a leaf or a node which doesn't have non-visited nodes |
| A node is fully explored before any other can begin | Exploration of a node is suspended as soon as another unexplored is found |
| Uses Queue data structure to store un-explored nodes | Uses Stack data structure to store un-explored nodes |
| BFS is slower and require more memory | DFS is faster and require less memory |

## Event Loop

The event loop is a single-threaded loop that monitors the call stack and checks if there is any work to be done in the task queue. If the call stack is empty and there are callback functions in the tack queue, a function is dequeued and pushed onto the call stack to be executed.

## Event Bubbling

When an event triggers on a DOM element, it will attempt to handle the vent if there is a listener attached, then the event is bubbled up to its parent and the same thing happens. The bubbling occurs up the element's ancestors all the way to the document. Event bubbling is the mechanism behind event delegation.

## Event Delegation

Event delegation is a technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant elements due to event bubbling up the DOM.

The benefits of this technique are:

* Memory footprint goes down because only one single handler is needed on the parent element, rather than having to attach event handlers on each descendant.
* There is no need to unbind the handler from elements that are removed and to bind the event for new elements. 

## Event Delegation vs Event Bubbling

Event delegation is a technique for listening to events where you delegate a parent element as the listener for all of the events that happen inside it.

Event bubbling is what the event itself does.

## How to stop Event bubbling and capturing during Event delegation

e.stopPropagation\(\)

## `setTimeout` and `setInterval`

setTimeout sets a timer which executes a function or specified piece of code once after the timer expires.

setInterval repeatedly calls a function or executes a code snippet, with a fixed time delay between each call.

## `setImmediate` vs `process.nextTick`

process.nextTick fires immediately on the same phase.

setImmediate fires on the following iteration or "tick" of the event loop.

## `new` vs `Object.create`

`new` is `Object.create` with additionally running the `constructor` function. And giving the `constructor` the chance to `return` the actual object that should be the result of the expression instead of `this`.

## Lexical Scope

Lexical scope, also known as static scope, is a convention that sets the scope of a variable so that it may only be called from within the block of code in which it is defined. The scope is determined when the code is compiled.

## Bind

The `bind` method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

## `Call` vs `Apply`

Both are used to invoke functions and the first parameter will be used as the value of `this` within the function. However, `call` takes in comma-separated arguments as the next arguments while `apply` takes in an array of arguments as the next argument.

## `Map` vs `forEach`

`forEach`: parameter is a function, apply the function to each item. It modifies the original array.

`map`: apply the function to all elements, function has two parameters, first is value, second is index. It returns a new array, the original array is not modified.

## Event-Driven Programming

event-driven programming a programming paradigm in which the flow of the program is determined by events such as user actions, sensor outputs, or messages from other programs or threads.

## Why Arrow Function is Convenient

Since the arrow function offers a very clean concise syntax and more intuitive scope and `this` binding.

## Using Promises instead of Callbacks - pros & cons

props:

* avoid callback hell which can be unreadable
* makes it easy to write sequential asynchronous code that is readable with `.then()`
* makes it easy to write parallel asynchronous code with `Promise.all()`

cons:

* slightly more complex code
* in older browsers where ES6 is not supported, you need to load a polyfill in order to use it

## Software Design Pattern

* Singleton
* Factory method
* Strategy
* Observer
* Builder
* Adapter
* State

## How can you make people not change the value

Object.freeze\(\)

## Strict Mode - pros & cons

"use strict" is a statement used to enable strict mode to entire scripts or individual functions. Strict mode is a way to opt into a restricted variant of JavaScript.

advantages:

* makes it impossible to accidentally create global variables
* makes assignments which would otherwise silently fail to throw an exception
* makes attempts to delete undeletable properties throw
* requires that function parameter names be unique
* this is undefined in the global context
* it catches some common coding bloopers, throwing exceptions
* it disables features that are confusing or poorly thought out

disadvantages

* many missing features that some developers might be used to
* no more access to function.caller and function.arguments
* concatenation of scripts written in different strict modes might cause issues

## What is module and how do you use that

A module is a separated part of a program. It helps developers to separate functionality and organize the codebase by using export and import.

## How to make JavaScript Multi-thread

HTML5 Web Workers

## 4 ways to Deep Copy Object

* Using iteration - not work for nested objects

```javascript
const iterationCopy = (obj) => {
    let res = {};
    for (let prop in obj) {
        if (obj.hasOwnProperty(prop)) {
            res[prop] = obj[prop];
        }
    }
    return res;
}
```

* Converting to JSON and back

```javascript
JSON.parse(JSON.stringify(obj));
```

* Using Object.assign - not work for nested objects

```javascript
Object.assign({}, obj);
```

* Using Spread Operator - not work for nested objects

```javascript
newObject = {...oldObject};
```

## How can you share code between files

On the client \(browser environment\), as long as the variables/functions are declared in the global scope, all scripts can refer to them.

On the server \(Node.js\), Each file is treated as a module and it can export variables and functions by attaching them to the `module.exports` object.

## Test Method

Jasmine


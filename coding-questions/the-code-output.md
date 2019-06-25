# Code Output

## How many times is the string "Hello" printed

```javascript
var x = 10;
if ((null) || (console.log("Hello")) || x > 5) {
    console.log("Hello");
}

// answer: 2
```

## What is the output of this code snippet

```javascript
function makeMultiplier(multiplier) {
  var myFunFunc = function (x) {
    return multiplier * x;
  };
  
  return myFunFunc;
}

var operation = makeMultiplier(10);
console.log(operation(10));

// answer: 100
```

## What is the output of this code snippet

```javascript
// funcObject - object instantiation & this tests
let Circle = function (radius) {
    this.radius = radius;

    this.getArea = function() {
        return Math.PI*Math.pow(this.radius, 2);
    }
}
// Note: new in call
let myCircleNew = new Circle(5);  // area - 78.5 for radius 5
console.log("myCircleNew...  logs");
console.log(myCircleNew.getArea());

// Note:  no new in call
let myCircleDirectCall = Circle(10); // area - 314.16 for radius 10
console.log("myCircleDirectCall...  logs");
console.log(myCircleDirectCall.getArea());

// answer: myCircleNew.getArea() returns 78.5;  
// myCircleDirectCall.getArea() fails with error
```

## What is the output of this code 

```javascript
var counter = 0;
var myArray = ["Yaakov", 2, {handle: "yaakovchaikin"}];
for (var i = 0; i < myArray.length; i++) {
  counter++;
}
console.log(counter);

// answer: 3
```

## What is the output of this code snippet

```javascript
// objLiteral and closures

let myLiteralObj = {
    age: 20,
    setAge: (newAge) => {
        this.age = newAge; //this指的是window，57
    },
    getAge: () => this.age, //this指的是window，57
    getSeniorStatusThroDirectAccess:  function() {
        if (this.age>55)    // Note direct attribute access，this指的是myLiteralObj，20
            return "Senior";
        else
            return("Not Senior")
    },
    getSeniorStatusThroGettor:  function() {
        if (this.getAge()>55)      // Note access via Gettor，57
            return "Senior";
        else
            return("Not Senior")
    },
}
myLiteralObj.setAge(57);
console.log("DirectAccess: " +
        myLiteralObj.getSeniorStatusThroDirectAccess());
console.log("Through gettor: " +
        myLiteralObj.getSeniorStatusThroGettor());
        
// answer: Output is “DirectAccess: Not Senior”  
// followed by “Through gettor: Senior”
```

## Immediately Invoked Function Execution: Given this code

```javascript
(function(window) {

  var obj = {};
  
  obj.dreamOn = function () {
    console.log("I want to see the global scope! Let me out!");
  };
  
  window.doer = obj;
  
 });
 
doer.dreamOn();

// answer: The attempted Immediately Invoked Function Execution (IIFE) is not being 
// invoked and passed in the window object. It's missing '(window)' Line 11 
// right before the semicolon.
```

## DOM manipulation: What will be the difference in the output between the 2 JavaScript code snippets

```javascript
<input id="name" type="text" value="Hi">

console.log(document.getElementById("name").value + " Hello world!");

console.log(document.querySelector("#name").value + " Hello world!");

// answer: no difference
```

## Events: What will the code snippet below do

```markup
...
<head>
<script>
document.addEventListener("DOMContentLoaded", function(event) {
  console.log("Yey!");
});
</script>
</head>
<body>
...
<h1>Hello!</h1>
</body>
</html>

// answer: It will output Yey! when the web page is loaded, but before 
// external resources like images are downloaded to ≠ user's machine.
```

## What is the output of this code

```javascript
const arr = [0, 1, 2, 3, 4];
for (var i = 0; i < arr.length; i++) {
    setTimeout(function() {
        console.log('Index: ' + i + ' value:' + arr[i]);
    }, 3000);
}

// Fix:
for (var i = 0; i < arr.length; i++) {
  (function(i) {
      setTimeout(function() {
          console.log('Index: ' + i + ' value:' + arr[i]);
      }, 3000);    
  })(i);
}

// output : 
// Index: 5 value:undefined
// Index: 5 value:undefined
// Index: 5 value:undefined
// Index: 5 value:undefined
// Index: 5 value:undefined
```

## What is the output of this code

```javascript
for (var i = 0; i< 5; i++) {
	setTimeout(() => console.log(i)); // 5 5 5 5 5
}

for (var i = 0; i< 5; i++) {
	setTimeout(() => console.log(i)); // 5 5 5 5 5 
}
setTimeout(() => console.log(i)); // 5

for (let i = 0; i< 5; i++) {
	setTimeout(() => console.log(i)); // 0 1 2 3 4
}

for (let i = 0; i< 5; i++) {
	setTimeout(() => console.log(i)); // 0 1 2 3 4
}
setTimeout(() => console.log(i)); // ERROR: i is not defined
```

## What is the output of this code

```javascript
test();
var n = 9;;

function test(){
 console.log(n); // undefined
}
console.log(n); // 9
```

## What is the output of this code

```javascript
var obj = {
  name: "Tom",
  age: 20
}

var dup = obj;
obj.age = 45;
obj={
  Class: "xxx",
}

console.log(dup.age);  // 45
console.log(obj.age);  // undefined 
console.log(obj.name); // undefined
```

## What is the output of this code

```javascript
var module = {
  x: 42,
  getX: () => {
    return this.x;
  }
}
var unbound = module.getX;
console.log(unbound()); // undefined 
var bound = unbound.bind(module);
console.log(bound());   // undefined
```

## What is the output of this code

```javascript
setTimeout(function() {
  console.log(1)
}, 0)
setTimeout(function() {
  console.log(2)
}, 0)
setTimeout(function() {
  console.log(3)
}, 100)
setTimeout(function() {
  console.log(4)
}, 100)
setTimeout(function() {
  console.log(5)
}, 0)

// answer: 1, 2, 5, 3, 4
```

## What is the output of this code

```javascript
function foo1() {
  return {
    bar: "hello"
  };
} // return an object

function foo2() {
  return 
  {
    bar: "hello"
  };
} // return undefined
```

## What is the output of this code

```javascript
(function(){
  var a = b = 3; // same as var a = b; b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined')); // false
console.log("b defined? " + (typeof b !== 'undefined')); // true
```

## What is the output of this code

```javascript
var myObject = {
    foo: "bar",
    func: function() {
        var self = this;
        console.log("outer func:  this.foo = " + this.foo); // bar
        console.log("outer func:  self.foo = " + self.foo); // bar
        (function() {
            console.log("inner func:  this.foo = " + this.foo); // undefined
            console.log("inner func:  self.foo = " + self.foo); // bar
        }());
    }
};
myObject.func();
```

## What is the output of this code

```javascript
var length = 10;
function fn() {
	console.log(this.length);
}

var obj = {
  length: 5,
  method: function(fn) {
    fn(); // 10 - the scope of this function is window
    arguments[0](); // 2 - the scope of this function is the arguments array
  }
};

obj.method(fn, 1);
```

## What is the output of this code

```javascript
(function () {
    try {
        throw new Error();
    } catch (x) {
        var x = 1, y = 2;
        console.log(x); // 1
    }
    console.log(x); // undefined, because there's two scopes for x, only the inner scope is defined. 
    console.log(y); // 2
})();
```

## What is the output of this code

```javascript
var x = 21;
var girl = function () {
    console.log(x); // undefined, since JavaScript initialization is not hoisted.
    var x = 20;
};
girl ();
```

## What is the output of this code

```javascript
const {
  a: aa,
  b: bb
} = {	
  aa: "a",
  a: "test",
  b: "bb",
  bb: "b"
}
console.log(a);   // reference error
console.log(aa);  // test
console.log(b);  // reference error
console.log(bb);  // bb
```


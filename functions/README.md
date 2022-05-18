## # FUNCTIONS

<br/>

## Q. ***What are fat arrow functions? When you should not use arrow functions in ES6?***

An arrow function is a shorter syntax for a function expression and does not have its own **this, arguments, super, or new.target**. These function are best suited for non-method functions, and they cannot be used as constructors.

**Arrow functions in ES6 has two limitations:**

* Don't work with new
* Fixed this bound to scope at initialisation

**When should not use Arrow Functions:** 

**1. Object methods**  
When you call cat.jumps, the number of lives does not decrease. It is because this is not bound to anything, and will inherit the value of this from its parent scope.
```js
var cat = {
  lives: 9,
  jumps: () => {
    this.lives--;
  }
}
```

**2. Callback functions with dynamic context:**  

If we click the button, we would get a TypeError. It is because this is not bound to the button, but instead bound to its parent scope.

```js
var button = document.getElementById('press');
button.addEventListener('click', () => {
  this.classList.toggle('on');
});
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the benefit of using the arrow syntax for a method in a constructor?***

The main advantage of using an arrow function as a method inside a constructor is that the value of `this` gets set at the time of the function creation and can\'t change after that. So, when the constructor is used to create a new object, `this` will always refer to that object.

```js
const Person = function(firstName) {
  this.firstName = firstName;
  this.sayName1 = function() { console.log(this.firstName); };
  this.sayName2 = () => { console.log(this.firstName); };
};

const john = new Person('John');
const dave = new Person('Dave');

john.sayName1(); // John
john.sayName2(); // John

// The regular function can have its 'this' value changed, but the arrow function cannot
john.sayName1.call(dave); // Dave (because "this" is now the dave object)
john.sayName2.call(dave); // John

john.sayName1.apply(dave); // Dave (because 'this' is now the dave object)
john.sayName2.apply(dave); // John

john.sayName1.bind(dave)(); // Dave (because 'this' is now the dave object)
john.sayName2.bind(dave)(); // John

var sayNameFromWindow1 = john.sayName1;
sayNameFromWindow1(); // undefined (because 'this' is now the window object)

var sayNameFromWindow2 = john.sayName2;
sayNameFromWindow2(); // John
```

The main takeaway here is that `this` can be changed for a normal function, but the context always stays the same for an arrow function. So even if you are passing around your arrow function to different parts of your application, you wouldn\'t have to worry about the context changing.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are the benefits of using arrow function over es5 function?***

Arrows is a new syntax for functions, which brings several benefits:

* Arrow syntax automatically binds `this` to the surrounding code’s context
* The syntax allows an implicit return when there is no body block, resulting in shorter and simpler code in some cases
* Last but not least, `=>` is shorter and simpler than `function`, although stylistic issues are often subjective

```js
//arrow function with no parameters
var a1 = () => 1;
 
//arrow with one parameter can be defined without parentheses
var a2 = x => 1;
var a3 = (x) => 1;
 
//arrow with multiple params requires parentheses
var a4 = (x, y) => 1;
 
//arrow with body has no implicit return
var a5 = x => { return 1; };
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a first class function?***

JavaScript functions are first-class functions meaning functions and objects are treated as the same thing. Functions can be stored as a variable inside an object or an array as well as it can be passed as an argument or be returned by another function. That makes function "first-class citizens in JavaScript"

**Example:** Assign a function to a variable

```js
const message = function() {
   console.log("Hello World!");
}

message(); // Invoke it using the variable
```

**Example:** Pass a function as an Argument

```js
function sayHello() {
   return "Hello, ";
}
function greeting(helloMessage, name) {
  console.log(helloMessage() + name);
}
// Pass `sayHello` as an argument to `greeting` function
greeting(sayHello, "JavaScript!");
```

**Example:** Return a function

```js
function sayHello() {
   return function() {
      console.log("Hello!");
   }
}
```

**Example:** Using a variable

```js
const sayHello = function() {
   return function() {
      console.log("Hello!");
   }
}
const myFunc = sayHello();
myFunc();
```

**Example:** Using double parentheses

```js
function sayHello() {
   return function() {
      console.log("Hello!");
   }
}
sayHello()();
```

We are using double parentheses `()()` to invoke the returned function as well.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a higher order function?***

A Higher-Order function is a function that receives a function as an argument or returns the function as output.

For example, `Array.prototype.map()`, `Array.prototype.filter()` and `Array.prototype.reduce()` are some of the Higher-Order functions in javascript.

```js
const arr1 = [1, 2, 3];
const arr2 = arr1.map(function(item) {
  return item * 2;
});
console.log(arr2);
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a unary function?***

Unary function (i.e. monadic) is a function that accepts exactly one argument. Let us take an example of unary function. It stands for single argument accepted by a function.

```js
const unaryFunction = a => console.log (a + 10); //Add 10 to the given argument and display the value
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is currying function?***

Currying is the process of taking a function with multiple arguments and turning it into a sequence of functions each with only a single argument.

```js
function volume(length) {
  return function(width) {
    return function(height) {
      return height * width * length;
    }
  }
}

volume(2)(3)(4); // 24
```

Curried functions are great to improve code re-usability and functional composition.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a pure function?***

Pure functions are functions that accept an input and returns a value without modifying any data outside its scope(Side Effects). Its output or return value must depend on the input/arguments and pure functions must return a value.

**Example:**

```js
function impure(arg) {
    finalR.s = 90
    return arg * finalR.s
}
```

The above function is not a pure function because it modified a state `finalR.s` outside its scope.

```js
function pure(arg) {
    return arg * 4
}
```

Here is a pure function. It didn\'t side effect any external state and it returns an output based on the input.

A function must pass two tests to be considered “pure”:

1. Same inputs always return same outputs
1. No side-effects

**1. Same Input => Same Output**  
Compare this:

```js
const add = (x, y) => x + y;

add(2, 4); // 6
```

To this

```js
let x = 2;

const add = (y) => {
  x += y;
};

add(4); // x === 6 (the first time)
```

**2. Pure Functions = Consistent Results:**

The first example returns a value based on the given parameters, regardless of where/when you call it.

If you pass 2 and 4, you’ll always get 6.

Nothing else affects the output.

**Benefits:**

* One of the major benefits of using pure functions is they are immediately testable. They will always produce the same result if you pass in the same arguments.
* The pure functions are easier to parallelize
* They also makes maintaining and refactoring code much easier.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is memoization in JavaScript?***

Memoization is a programming technique which attempts to increase a function’s performance by caching its previously computed results.  Each time a memoized function is called, its parameters are used to index the cache. If the data is present, then it can be returned, without executing the entire function. Otherwise the function is executed and then the result is added to the cache.

```js
// A simple memoized function to Add Number
const memoizedAdd = () => {
  let cache = {};
  return (number) => {
    if (number in cache) {
      console.log('Fetching from cache: ');
      return cache[number];
    }
    else {
      console.log('Calculating result: ');
      let result = number + 10;
      cache[number] = result;
      return result;
    }
  }
}
// returned function from memoizedAdd
const sum = memoizedAdd();

console.log(sum(10)); // Calculating result: 20
console.log(sum(10)); // Fetching from cache: 20
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is an arguments object?***

The arguments object is an Array-like object accessible inside functions that contains the values of the arguments passed to that function. For example, let us see how to use arguments object inside sum function,

```js
function sum() {
    var total = 0;
    for (var i = 0, len = arguments.length; i < len; ++i) {
        total += arguments[i];
    }
    return total;
}

sum(1, 2, 3) // returns 6
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Can we define properties for functions?***

Yes, We can define properties for functions because functions are also objects.

```js
fn = function(x) {
  //Function code goes here
}

fn.name = "John";

fn.profile = function(y) {
  //Profile code goes here
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the way to find the number of parameters expected by a function?***

You can use `function.length` syntax to find the number of parameters expected by a function. Let us take an example of `sum` function to calculate the sum of numbers,

```js
function sum(num1, num2, num3, num4){
    return num1 + num2 + num3 + num4;
}
sum.length // 4 is the number of parameters expected.
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the difference between Call, Apply and Bind?***

**call():**

The call() method invokes a function with a given `this` value and arguments provided one by one

```js
var employee1 = {firstName: 'John', lastName: 'Rodson'};
var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

function invite(greeting1, greeting2) {
    console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
}

invite.call(employee1, 'Hello', 'How are you?'); // Hello John Rodson, How are you?
invite.call(employee2, 'Hello', 'How are you?'); // Hello Jimmy Baily, How are you?
```

**apply():**

Invokes the function and allows you to pass in arguments as an array

```js
var employee1 = {firstName: 'John', lastName: 'Rodson'};
var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

function invite(greeting1, greeting2) {
    console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
}

invite.apply(employee1, ['Hello', 'How are you?']); // Hello John Rodson, How are you?
invite.apply(employee2, ['Hello', 'How are you?']); // Hello Jimmy Baily, How are you?
```

**bind():**

returns a new function, allowing you to pass in an array and any number of arguments

```js
var employee1 = {firstName: 'John', lastName: 'Rodson'};
var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

function invite(greeting1, greeting2) {
    console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
}

var inviteEmployee1 = invite.bind(employee1);
var inviteEmployee2 = invite.bind(employee2);

inviteEmployee1('Hello', 'How are you?'); // Hello John Rodson, How are you?
inviteEmployee2('Hello', 'How are you?'); // Hello Jimmy Baily, How are you?
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the difference between `.call` and `.apply`?***

Both `.call` and `.apply` are used to invoke functions and the first parameter will be used as the value of `this` within the function. However, `.call` takes in comma-separated arguments as the next arguments while `.apply` takes in an array of arguments as the next argument. An easy way to remember this is C for `call` and comma-separated and A for `apply` and an array of arguments.

```js
function add(a, b) {
  return a + b;
}

console.log(add.call(null, 1, 2)); // 3
console.log(add.apply(null, [1, 2])); // 3
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Explain `Function.prototype.bind`?***

[MDN](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Function/bind):

> The `bind()` method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

In my experience, it is most useful for binding the value of `this` in methods of classes that you want to pass into other functions. This is frequently done in React components.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***YO-What is an anonymous function?***

An anonymous function is a function without a name! Anonymous functions are commonly assigned to a variable name or used as a callback function. The syntax would be as below,

```js
function (optionalParameters) {
  //do something
}

const myFunction = function(){ //Anonymous function assigned to a variable
  //do something
};

[1, 2, 3].map(function(element){ //Anonymous function used as a callback function
  //do something
});
```

Example:

```js
var x = function (a, b) {return a * b};
var z = x(5, 10);
console.log(z); // 50
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a typical use case for anonymous functions?***

They can be used in IIFEs to encapsulate some code within a local scope so that variables declared in it do not leak to the global scope.

```js
(function() {
  // Some code here.
})();
```

As a callback that is used once and does not need to be used anywhere else. The code will seem more self-contained and readable when handlers are defined right inside the code calling them, rather than having to search elsewhere to find the function body.

```js
setTimeout(function() {
  console.log('Hello world!');
}, 1000);
```

Arguments to functional programming constructs or Lodash (similar to callbacks).

```js
const arr = [1, 2, 3];
const double = arr.map(function(el) {
  return el * 2;
});

console.log(double); // [2, 4, 6]
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`?******

The former is a function declaration while the latter is a function expression. The key difference is that function declarations have its body hoisted but the bodies of function expressions are not (they have the same hoisting behavior as variables). For more explanation on hoisting, refer to the question above [on hoisting](#explain-hoisting). If you try to invoke a function expression before it is defined, you will get an `Uncaught TypeError: XXX is not a function` error.

**Function Declaration:**

```js
foo(); // 'FOOOOO'
function foo() {
  console.log('FOOOOO');
}
```

**Function Expression:**

```js
foo(); // Uncaught TypeError: foo is not a function
var foo = function() {
  console.log('FOOOOO');
};
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***YO-What is the definition of a higher-order function?***

A higher-order function is any function that takes one or more functions as arguments, which it uses to operate on some data, and/or returns a function as a result. Higher-order functions are meant to abstract some operation that is performed repeatedly. The classic example of this is `map`, which takes an array and a function as arguments. `map` then uses this function to transform each item in the array, returning a new array with the transformed data. Other popular examples in JavaScript are `forEach`, `filter`, and `reduce`. A higher-order function doesn\'t just need to be manipulating arrays as there are many use cases for returning a function from another function. `Function.prototype.bind` is one such example in JavaScript.

**Map:**

Let say we have an array of names which we need to transform each string to uppercase.

```js
const names = ['irish', 'daisy', 'anna'];
```

The imperative way will be as such:

```js
const transformNamesToUppercase = function(names) {
  const results = [];
  for (let i = 0; i < names.length; i++) {
    results.push(names[i].toUpperCase());
  }
  return results;
};
transformNamesToUppercase(names); // ['IRISH', 'DAISY', 'ANNA']
```

Use `.map(transformerFn)` makes the code shorter and more declarative.

```js
const transformNamesToUppercase = function(names) {
  return names.map(name => name.toUpperCase());
};
transformNamesToUppercase(names); // ['IRISH', 'DAISY', 'ANNA']
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Can you give an example of a curry function and why this syntax offers an advantage?***

Currying is a pattern where a function with more than one parameter is broken into multiple functions that, when called in series, will accumulate all of the required parameters one at a time. This technique can be useful for making code written in a functional style easier to read and compose. It is important to note that for a function to be curried, it needs to start out as one function, then broken out into a sequence of functions that each accepts one parameter.

```js
function curry(fn) {
  if (fn.length === 0) {
    return fn;
  }

  function _curried(depth, args) {
    return function(newArgument) {
      if (depth - 1 === 0) {
        return fn(...args, newArgument);
      }
      return _curried(depth - 1, [...args, newArgument]);
    };
  }

  return _curried(fn.length, []);
}

function add(a, b) {
  return a + b;
}

var curriedAdd = curry(add);
var addFive = curriedAdd(5);

var result = [0, 1, 2, 3, 4, 5].map(addFive); // [5, 6, 7, 8, 9, 10]
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the difference between a method and a function in javascript?***

In JS, that difference is quite subtle. A function is a piece of code that is called by name and function itself not associated with any object and not defined inside any object. It can be passed data to operate on (i.e. parameter) and can optionally return data (the return value).

```js
// Function statement
function myFunc() {
  // Do some stuff;
}

// Calling the function
myFunc();
```

Here myFunc() function call is not associated with object hence not invoked through any object.

A function can take a form of immediately invoked function expression (IIFE):

```js

// Anonymous Self-invoking Function
(function() {
  // Do some stuff;
})();
```

Finally there are also arrow functions:

```js
const myFunc = arg => {
    console.log("hello", arg)
} 
```

A method is a piece of code that is called by its name and that is associated with the object. Methods are functions. When you call a method like this `obj1.myMethod()`, the reference to `obj1` gets assigned (bound) to `this` variable. In other words, the value of `this` will be `obj1` inside `myMethod`.

Here are some examples of methods:

**Example 1:**

```js
var obj1 = {
  attribute: "xyz",
  myMethod: function () {  // Method
    console.log(this.attribute);
  }
};

// Call the method
obj1.myMethod();
```

Here `obj1` is an object and `myMethod` is a method which is associated with `obj1`.

**Example 2:**

In ES6 we have classes. There the methods will look like this:

```js
class MyAwesomeClass {
  myMethod() {
    console.log("hi there");
  }
}

const obj1 = new MyAwesomeClass();
obj1.myMethod();
```

Understand: the method is not some kind of special type of a function, and It is not about how you declare a function. It is the way we **call** a function. Look at that: 

```js
var obj1 = {
  prop1: "buddy"
}; 
var myFunc = function () {
  console.log("Hi there", this);
};
// Let us call myFunc as a function: 
myFunc(); // will output "Hi there undefined" or "Hi there Window"
 
obj1.myMethod = myFunc;
//now we're calling myFunc as a method of obj1, so this will point to obj1
obj1.myMethod(); // will print "Hi there" following with obj1. 
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is typical use case for anonymous function in JavaScript?***

Anonymous functions basically used in following scenario.

a.) No name is needed if function is only used in one place, then there is no need to add a name to function.

Example: setTimeout function

```js
setTimeout(function(){
	alert("Hello");
},1000);
```
Here there is no need of using named function when we are sure 	that function which will alert `hello` would use only once in	application.

b.) Anonymous functions are declared inline and inline functions have advantages in the case that they can access variable in the parent scopes.

Let us take a example of event handler. Notify event of particular 	type (such as click) for a given object. 

Let say we have HTML element (button) on which we want to add click event and when user do click on button we would like toexecute some logic.

```html
<button id="myBtn"></button>
```
Add Event Listener 

```js
var btn = document.getElementById('myBtn');
btn.addEventListener('click', function () {
  alert('button clicked');
});
```
	
Above example shows used of anonymous function as a callback function in event handler.
	
c.) Passing anonymous function as a parameter to calling function.
	
**Example:** 

```js
// Function which will execute callback function
function processCallback(callback){
	if(typeof callback === 'function'){
		callback();
	}
}

// Call function and pass anonymous function as callback 
processCallback(function(){
	alert("Hi I am anonymous callback function");
});
```
The best way to make a decision for using anonymous function is to ask the following question:

Will the function which I am going to define, be used anywhere else?***

If your answer is yes then go and create named function rather anonymous function.

**Advantage of using anonymous function:**

* It can reduce a bit of code, particularly in recursive function and in callback function.
* Avoid needless global namespace pollutions.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is Function binding?***

 Function binding falls in advance JavaScript category and this is very popular technique to use in conjunction with event handler and callback function to preserve code execution context while passing function as a parameter.

Example:

```js
var clickHandler = {
	message: 'click event handler',
	handleClick: function(event) {
		console.log(this.message);
	}
};

var btn = document.getElementById('myBtn');
// Add click event to btn
btn.addEventListener('click', clickHandler.handleClick);
```

Here in this example clickHandler object is created which contain message properties and handleClick method.

We have assigned handleClick method to a DOM button, which will be executed in response of click. When the button is clicked, then handleClick method is being called and console message. Here console.log should log the `click event handler` message but it actually log `undefined`.

The problem of displaying `undefined` is because of the execution context of clickHandler.handleClick method is not being saved hence `this` pointing to button `btn` object. We can fix this issue using bind method.

```js
var clickHandler = {
	message: 'click event handler',
	handleClick: function(event) {
		console.log(this.message);
	}
};

var btn = document.getElementById('myBtn');
// Add click event to btn and bind the clickHandler object
btn.addEventListener('click', clickHandler.handleClick.bind(clickHandler));
```

`bind` method is available to all the function similar to call and apply method which take argument value of `this`.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Explain how `this` works in JavaScript?***

The following rules are applied when we use `this` keyword in javascript

1. If the `new` keyword is used when calling the function, `this` inside the function is a brand new object.
2. If `apply`, `call`, or `bind` are used to call/create a function, `this` inside the function is the object that is passed in as the argument.
3. If a function is called as a method, such as `obj.method()` — `this` is the object that the function is a property of.
4. If a function is invoked as a free function invocation, meaning it was invoked without any of the conditions present above, `this` is the global object. In a browser, it is the `window` object. If in strict mode (`'use strict'`), `this` will be `undefined` instead of the global object.
5. If multiple of the above rules apply, the rule that is higher wins and will set the `this` value.
6. If the function is an ES2015 arrow function, it ignores all the rules above and receives the `this` value of its surrounding scope at the time it is created.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is generator in JS?***

**Generator-Function:**

A generator-function is defined like a normal function, but whenever it needs to generate a value, it does so with the `yield` keyword rather than `return`. The `yield` statement suspends function’s execution and sends a value back to caller, but retains enough state to enable function to resume where it is left off. When resumed, the function continues execution immediately after the last `yield` run.

Syntax 

```js
function* gen() {
     yeild 1;
     yeild 2;
     ...
     ...
}
```

**Generator-Object:** 

Generator functions return a generator object. Generator objects are used either by calling the next method on the generator object or using the generator object in a “for in” loop.

```js
function * fun() {
    yield 10;
    yield 20;
    yield 30;
} 
  
// Calling the Generate Function
var gen = fun();
document.write(gen.next().value);
document.write("<br>");
document.write(gen.next().value);
document.write("<br>");
document.write(gen.next().value);
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Compare Async-Await and Generators usage to achive same functionality?***

**Generators/Yield**

Generators are objects created by generator functions — functions with an * (asterisk) next to their name. The yield keyword pauses generator function execution and the value of the expression following the yield keyword is returned to the generator's caller. It can be thought of as a generator-based version of the return keyword.
```js
const generator = (function*() {
  // waiting for .next()
  const a = yield 5;
  // waiting for .next()
  console.log(a); // => 15
})();

console.log(generator.next()); // => { done: false, value: 5 }
console.log(generator.next(15)); // => { done: true, value: undefined }
```
**Async/Await**

Async keyword is used to define an asynchronous function, which returns a `AsyncFunction` object.

Await keyword is used to pause async function execution until a `Promise` is fulfilled, that is resolved or rejected, and to resume execution of the `async` function after fulfillments. When resumed, the value of the `await` expression is that of the fulfilled `Promise`.

**Key points:**  

1. Await can only be used inside an async function.
2. Functions with the async keyword will always return a promise.
3. Multiple awaits will always run in sequential order under a same function.
4. If a promise resolves normally, then await promisereturns the result. But in case of a rejection it throws the error, just if there were a throw statement at that line.
5. Async function cannot wait for multiple promises at the same time.
6. Performance issues can occur if using await after await as many times one statement doesn\'t depend on the previous one.

```js

async function asyncFunction() {

  const promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("i am resolved!"), 1000)
  });

  const result = await promise; 
  // wait till the promise resolves (*)

  console.log(result); // "i am resolved!"
}

asyncFunction();
```

**Generator and Async-await — Comparison**  

1. Generator functions/yield and Async functions/await can both be used to write asynchronous code that “waits”, which means code that looks as if it was synchronous, even though it really is asynchronous.
2. Generator function are executed yield by yield i.e one yield-expression at a time by its iterator (the next method) where as Async-await, they are executed sequential await by await.
3. Async/await makes it easier to implement a particular use case of Generators.
4. The return value of Generator is always {value: X, done: Boolean} where as for Async function it will always be a promise that will either resolve to the value X or throw an error.
5. Async function can be decomposed into Generator and promise implementation which are good to know stuff.

Generators and async functions always return a specific type of object:
- Generator functions: If you yield/return a value X, it will always return an iteration object with the form {value: X, done: Boolean}
- Async functions: If you return a value X, it will always return a promise that will either resolve to the value X or throw an error.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How do you compare two date objects?***

You need to use use date.getTime() method to compare date values instead comparision operators (==, !=, ===, and !== operators)

```js
var d1 = new Date();
var d2 = new Date(d1);
console.log(d1.getTime() === d2.getTime()); //True
console.log(d1 === d2); // False
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is difference between document.getElementById() and document.querySelector()?***

* **document.getElementById()**

Returns an element object representing the element whose id property matches the specified string. Since element IDs are required to be unique if specified, they're a useful way to get access to a specific element quickly.

```js
element = document.getElementById(id);
```

* **document.querySelector()**

Returns the first matching Element node within the node\'s subtree. If no matching node is found, null is returned.

```js
element = document.querySelector(selectors);
```

* **document.querySelectorAll()**

Returns a NodeList containing all matching Element nodes within the node\'s subtree, or an empty NodeList if no matches are found.

```js
element = document.querySelectorAll(selectors);
```

*Note: `querySelector()` is more useful when we want to use more complex selectors*.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are closures?***

A closure is the combination of a function and the lexical environment within which that function was declared. i.e, It is an inner function that has access to the outer or enclosing function\'s variables. The closure has three scope chains

* Own scope where variables defined between its curly brackets
* Outer function’s variables
* Global variables

```js
function Welcome(name) {
  var greetingInfo = function(message) {
    console.log(message+' '+name);
  }
  return greetingInfo;
}
var myFunction = Welcome('John');
myFunction('Welcome '); // Output: Welcome John
myFunction('Hello Mr.'); // output: Hello Mr.John
```

As per the above code, the inner `function greetingInfo()` has access to the variables in the outer `function Welcome()` even after outer function has returned.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Name the two functions that are used to create an HTML element dynamically?***

**createElement**  
In an HTML document, the `document.createElement()` method creates the HTML element specified by tagName.
Syntax

```js
var element = document.createElement(tagName[, options]);
```

HTML

```html
<!DOCTYPE html>
<html>
  <head>
      <title>||Working with elements||</title>
  </head>
<body>
  <div id="div1">The text above has been created dynamically.</div>
</body>
</html>
```

JavaScript

```js
document.body.onload = addElement;

function addElement () { 
  // create a new div element 
  var newDiv = document.createElement("div"); 
  // and give it some content 
  var newContent = document.createTextNode("Hi there and greetings!"); 
  // add the text node to the newly created div
  newDiv.appendChild(newContent);  

  // add the newly created element and its content into the DOM 
  var currentDiv = document.getElementById("div1"); 
  document.body.insertBefore(newDiv, currentDiv); 
}
```

**Create Dynamic Button:**

```js
var btn = document.createElement("BUTTON");
btn.innerHTML = "CLICK ME";
document.body.appendChild(btn);
```

**Removing Elements Dynamically:** 

```js
function removeElement(elementId) {
    // Removes an element from the document
    var element = document.getElementById(elementId);
    element.parentNode.removeChild(element);
}
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is callback() function in javascript?***

A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

```js
function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

processUserInput(greeting);
```

The above example is a synchronous callback, as it is executed immediately.

*Note: callbacks are often used to continue code execution after an asynchronous operation has completed — these are called asynchronous callbacks. A good example is the callback functions executed inside a `.then()` block chained onto the end of a promise after that promise fulfills or rejects. This structure is used in many modern web APIs, such as `fetch()`*.

In JavaScript, functions are objects. Because of this, functions can take functions as arguments, and can be returned by other functions. Functions that do this are called `higher-order` functions. Any function that is passed as an argument is called a callback function.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***When to use function declarations and expressions in JavaScript?***

**Function Declarations:**

A declared function is “saved for later use”, and will be executed later, when it is invoked (called).

```js
// Function declaration
function add(num1, num2) {
	return num1 + num2;
}
```

function is only declared here. For using it, it must be invoked using function name. e.g add(10, 20);  

**Function Expression:**

A function expression can be stored in a variable:

```js
// Function expression
var add = function (num1, num2) {
	return num1 + num2;
};
```

After a function expression has been stored in a variable, the variable can be used as a function. Functions stored in variables do not need function names. They are always invoked (called) using the variable name.

**Difference:**

* `Function declarations` load before any code is executed while `Function expressions` load only when the interpreter reaches that line of code.
* Similar to the `var` statement, function declarations are hoisted to the top of other code. Function expressions aren\'t hoisted, which allows them to retain a copy of the local variables from the scope where they were defined.  

**Benefits of Function Expressions:**  

There are several different ways that function expressions become more useful than function declarations.

* As closures
* As arguments to other functions
* As Immediately Invoked Function Expressions (IIFE)

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How to avoid callback hell in javascript?***

**Callback hell** is a phenomenon that afflicts a JavaScript developer when he tries to execute multiple asynchronous operations one after the other. Some people call it to be the **pyramid of doom**.  

Example

```js
doSomething(param1, param2, function(err, paramx){
    doMore(paramx, function(err, result){
        insertRow(result, function(err){
            yetAnotherOperation(someparameter, function(s){
                somethingElse(function(x){
                });
            });
        });
    });
});
```

**Techniques for avoiding callback hell:**  

* Write comments
* Split functions into smaller functions
* Using Async.js
* Using Promises
* Using Async-Await

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a callback function?***

A callback function is a function passed into another function as an argument. This function is invoked inside the outer function to complete an action.

```js
function callbackFunction(name) {
  console.log('Hello ' + name);
}

function outerFunction(callback) {
  let name = prompt('Please enter your name.');
  callback(name);
}

outerFunction(callbackFunction);
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Why do we need callbacks?***

The callbacks are needed because javascript is a event driven language. That means instead of waiting for a response javascript will keep executing while listening for other events.

Let us take an example with first function invoking an API call(simulated by setTimeout) and next function which logs the message.

```js
function firstFunction() {
  // Simulate a code delay
  setTimeout( function() {
    console.log('First function called');
  }, 1000 );
}
function secondFunction() {
  console.log('Second function called');
}
firstFunction();
secondFunction();

Output
// Second function called
// First function called
```

As observed from the output, javascript didnot wait for the response of first function and remaining code block get executed. So callbacks used in a way to make sure that certain code does not execute until other code finished execution.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is a callback hell?***

Callback Hell is an anti-pattern with multiple nested callbacks which makes code hard to read and debug when dealing with asynchronous logic. The callback hell looks like below,

```js
async1(function() {
    async2(function() {
        async3(function() {
            async4(function() {
                ....
            });
        });
    });
});
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is callback in callback?***

You can nest one callback inside in another callback to execute the actions sequentially one by one. This is known as callbacks in callbacks.

```js
loadScript('/script1.js', function(script) {
    console.log('first script is loaded');

  loadScript('/script2.js', function(script) {

    console.log('second script is loaded');

    loadScript('/script3.js', function(script) {

        console.log('third script is loaded');
      // after all scripts are loaded
    });
  })
});
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>
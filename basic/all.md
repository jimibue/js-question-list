## Q. ***List out important features of JavaScript ES6?***

**1. Template Strings:**

Template literals are string literals allowing embedded expressions.

**Benefits:**

* String interpolation
* Embedded expressions
* Multiline strings without hacks
* String formatting
* String tagging for safe HTML escaping, localization and more

```js
// String Substitution
let name = `Abhinav Sharma`;
console.log(`Hi, ${name}!`); // Output: "Abhinav Sharma"

// Multiline String
let msg = `Hello \
World`;
console.log(`${msg}`); // Output: "Hello World"
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-template-strings-dwj699?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**2. Spread Operator:**

Spread operator allows iterables( arrays / objects / strings ) to be expanded into single arguments/elements. 

```js
function sum(x, y, z) {
  return x + y + z;
}
const numbers = [10, 20, 30];

// Using Spread Operator
console.log(sum(...numbers)); // 60

// Using Apply (ES5)
console.log(sum.apply(null, numbers)); // 60
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-spread-operator-25tmcf?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**2.1. Copying an array:**

```js
let fruits = ["Apple", "Orange", "Banana"];
let newFruitArray = [...fruits];

console.log(newFruitArray); 

//Output 
['Apple','Orange','Banana']
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-spread-operator-wy1q0l?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**2.2. Concatenating arrays:**  

```js
let arr1 = ["A", "B", "C"];
let arr2 = ["X", "Y", "Z"];

let result = [...arr1, ...arr2];

console.log(result); 

// Output
['A', 'B', 'C', 'X', 'Y', 'Z']
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-spread-operator-m7v6gg?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**2.3. Spreading elements together with an individual element:**

```js
let fruits = ["Apple", "Orange", "Banana"];

let newFruits = ["Cherry", ...fruits];

console.log(newFruits); 

// Output
['Cherry', 'Apple','Orange','Banana']
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-spread-operator-16l7oh?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**2.4. Spreading elements on function calls:**

```js
let fruits = ["Apple", "Orange", "Banana"];

const getFruits = (f1, f2, f3) => {
  console.log(`Fruits: ${f1}, ${f2} and ${f3}`);
};

getFruits(...fruits); 

// Output
Fruits: Apple, Orange and Banana
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-spread-operator-jdhoe6?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**2.5. Spread syntax for object literals:**

```js
var obj1 = { id: 101, name: 'Rajiv Sandal' }
var obj2 = { age: 35, country: 'INDIA'}

const employee = { ...obj1, ...obj2 }

console.log(employee); // { "id": 101, "name": "Rajiv Sandal", "age": 35, "country": "INDIA" }
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**3. Sets:**  

Sets are a new object type with ES6 (ES2015) that allow to create collections of unique values. The values in a set can be either simple primitives like strings or integers, but more complex object types like object literals or arrays can also be part of a set.

```js
let numbers = new Set([10, 20, 20, 30, 40, 50]);

console.log(numbers); // Set(5) {10, 20, 30, 40, 50}
console.log(typeof numbers); // Object
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-sets-chwvp0)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**4. Default Parametrs:**

```js
function add(x = 10, y = 20) {
  console.log(x + y);
}

add(10, 30); // 40
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-default-parametrs-tjw9uk?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**5. repeat():**  

The `repeat()` method constructs and returns a new string which contains the specified number of copies of the string on which it was called, concatenated together.

```js
const msg = "Hello World \n";

console.log(`${msg.repeat(3)}`);

// Output: 
Hello World
Hello World
Hello World
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-repeat-d3ko3z?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**6. Arrow Function (=>):**

```js
let add = (x, y) => x + y;

console.log(add(10, 20)); // 30
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-arrow-function-ejlrmf?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**7. Arrow function with `this`**

```js
var person = {
  name: "Diksha",
  actions: ["bike", "hike", "ski", "surf"],
  printActions: function() {
    var _this = this;
    this.actions.forEach(function(action) {
      var str = _this.name + " likes to " + action;
      console.log(str);
    });
  }
};
person.printActions();

// Arrow function
let person = {
  name: "Diksha",
  actions: ["bike", "hike", "ski", "surf"],
  printActions() {
    this.actions.forEach((action) => {
      let str = this.name + " likes to " + action;
      console.log(str);
    });
  }
};

person.printActions();

// Output:
Diksha likes to bike 
Diksha likes to hike 
Diksha likes to ski 
Diksha likes to surf
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-arrow-function-kh1v84?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**8. Destructing Assignment:**

```js
const phone = {
  title: "iPhone",
  price: 999,
  description: "The iPhone is a smartphone developed by Apple"
};
console.log(phone.title);


// Destructing Assignment
const { title, price, description } = {
  title: "iPhone",
  price: 999,
  description: "The iPhone is a smartphone developed by Apple"
};
console.log(title); // iPhone
console.log(price); // 999
console.log(description); // The iPhone is a smartphone developed by Apple
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-destructing-assignment-0c0fzl?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**9. Generators:**  

A generator is a function that can stop midway and then continue from where it stopped. In short, a generator appears to be a function but it behaves like an `iterator`.

```js
function* generator(num) {
  yield num + 10;
  yield num + 20;
  yield num + 30;
}
let gen = generator(10);

console.log(gen.next().value); // 20
console.log(gen.next().value); // 30
console.log(gen.next().value); // 40
```  

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-generators-pboss2?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**10. Symbols:**  

They are tokens that serve as unique IDs. We create symbols via the factory function Symbol(). Symbols primary use case is for making private object properties, which can be only of type String or Symbol (Numbers are automatically converted to Strings).

```js
const symbol1 = Symbol();
const symbol2 = Symbol(42);
const symbol3 = Symbol("Hi");

console.log(typeof symbol1); // symbol
console.log(symbol3.toString()); // Symbol(Hi)
console.log(Symbol("Hi") === Symbol("Hi")); // false
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-symbols-5oedjv?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

**11. Iterator:**  
  
The iterable is a interface that specifies that an object can be accessible if it implements a method who is key is `[symbol.iterator]`.

```js
const title = "ES6";
const iterateIt = title[Symbol.iterator]();

console.log(iterateIt.next().value); //output: E
console.log(iterateIt.next().value); //output: S
console.log(iterateIt.next().value); //output: 6
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-iterator-ceqbrw?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## # VARIABLES

<br/>

## Q. ***What are global variables?***

Global variables are declared outside of a function or declared with a window object for accessibility throughout the program (unless shadowed by locals). If you declare a variable without using var, even if it\'s inside a function, it will still be seen as global.

The `var` **statement** declares a function-scoped or globally-scoped variable, optionally initializing it to a value.

**Example:**

```js
var x = 10;

if (x === 10) {
  var x = 20;

  console.log(x);
  // expected output: 20
}

console.log(x);
// expected output: 20
```

**Example:** Declaring global variable within function

```js
window.value = 90;

// Declaring global variable by window object
function setValue() {
  window.value = 100;
}

// Accessing global variable from other function
function getValue() {
  setValue();
  return window.value;
}

console.log(getValue()); // 100
```

**Using Undeclared Variables:**

* In strict mode, if you attempt to use an undeclared variable, you\'ll get a reference error when you run your code. 
* Outside of strict mode, however, if you assign a value to a name that has not been declared with `let`, `const`, or `var`, you\'ll end up creating a new global variable. It will be global no matter how deeply nested within functions and blocks your code is, which is almost certainly not what you want, is bug-prone, and is one of the best reasons for using strict mode!
* Global variables created in this accidental way are like global variables declared with `var`: they define properties of the global object. But unlike the properties defined by proper var declarations, these properties can be deleted with the delete operator.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-global-variables-b4isqk?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are template literals in es6?***

Template literals help make it simple to do string interpolation, or to include variables in a string.

```js
const person = { name: 'Tyler', age: 28 };

console.log(`Hi, my name is ${person.name} and I am ${person.age} years old!`);
// 'Hi, my name is Tyler and I am 28 years old!'
```

Template literals, however, preserve whatever spacing you add to them. For example, to create that same multi-line output that we created above, you can simply do:

```js
console.log(`This is line one.
This is line two.`);
// This is line one.
// This is line two.
```

Another use case of template literals would be to use as a substitute for templating libraries for simple variable interpolations:

```js
const person = { name: 'Tyler', age: 28 };

document.body.innerHTML = `
  <div>
    <p>Name: ${person.name}</p>
    <p>Name: ${person.age}</p>
  </div>
`
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What are the differences between variables created using `let`, `var` or `const`?***

Variables declared using the `var` keyword are scoped to the function in which they are created, or if created outside of any function, to the global object. `let` and `const` are _block scoped_, meaning they are only accessible within the nearest set of curly braces (function, if-else block, or for-loop).

```js
/**
 * All variables are accessible within functions.
 * 
**/
function variableScope() {

  var x = 10;
  let y = 20;
  const z = 30;

  console.log(x); // 10
  console.log(y); // 20
  console.log(z); // 30
}

console.log(x); // ReferenceError: x is not defined
console.log(y); // ReferenceError: y is not defined
console.log(z); // ReferenceError: z is not defined

variableScope();
```

```js
/**
 * var declared variables are accessible anywhere in the function scope.
 * 
 **/
if (true) {
  var a = 10;
  let b = 20;
  const c = 30;
}

console.log(a); // 10
console.log(b); // ReferenceError: baz is not defined
console.log(c); // ReferenceError: qux is not defined
```

`var` allows variables to be hoisted, meaning they can be referenced in code before they are declared. `let` and `const` will not allow this, instead throwing an error.

```js
console.log(foo); // undefined
var foo = 'foo';

console.log(baz); // ReferenceError: can't access lexical declaration 'baz' before initialization
let baz = 'baz';

console.log(bar); // ReferenceError: can't access lexical declaration 'bar' before initialization
const bar = 'bar';
```

Redeclaring a variable with `var` will not throw an error, but 'let' and 'const' will.

```js
var foo = 'foo';
var foo = 'bar';
console.log(foo); // "bar"

let baz = 'baz';
let baz = 'qux'; // Uncaught SyntaxError: Identifier 'baz' has already been declared
```

`let` and `const` differ in that `let` allows reassigning the variable's value while `const` does not.

```js
// This is fine.
let foo = 'foo';
foo = 'bar';

// This causes an exception.
const baz = 'baz';
baz = 'qux';
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-variables-declaration-fmrkjz?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is Hoisting in JavaScript?***

JavaScript **Hoisting** refers to the process whereby the interpreter appears to move the declaration of functions, variables or classes to the top of their scope, prior to execution of the code.

Hoisting allows functions to be safely used in code before they are declared.

**Example 01:** Function Hoisting

One of the advantages of hoisting is that it lets you use a function before you declare it in your code.

```js
getName("Sadhika Sandal");

function getName(name) {
  console.log("Hello " + name);
}

// Output
Hello Sadhika Sandal
```

**Example 02:** Variable Hoisting  

```js
console.log(message); // output : undefined
var message = "The variable Has been hoisted";
```

The above code looks like as below to the interpreter,

```js
var message;
console.log(message);
message = "The variable Has been hoisted";
```

**Example 03:** `let` and `const` hoisting

All declarations (function, var, let, const and class) are hoisted in JavaScript, while the `var` declarations are initialized with `undefined`, but `let` and `const` declarations remain uninitialized.

```js
console.log(x);
let x = 10;

// Output: ReferenceError: x is not defined
```

They will only get initialized when their lexical binding (assignment) is evaluated during runtime by the JavaScript engine. This means we can\'t access the variable before the engine evaluates its value at the place it was declared in the source code. This is what we call **Temporal Dead Zone**, A time span between variable creation and its initialization where they can\'t be accessed.

*Note: JavaScript only hoists declarations, not initialisation*

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-hoisting-l745nc?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the Temporal Dead Zone in ES6?***

In ES6, let bindings are not subject to Variable Hoisting, which means that let declarations do not move to the top of the current execution context. Referencing the variable in the block before the initialization results in a `ReferenceError` (contrary to a variable declared with var, which will just have the undefined value). The variable is in a “temporal dead zone” from the start of the block until the initialization is processed.

```javascript
console.log(aVar); // undefined
console.log(aLet); // causes ReferenceError: aLet is not defined
var aVar = 1;
let aLet = 2;
```

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the purpose of double exclamation?***

The double exclamation or negation(!!) ensures the resulting type is a boolean. If it was falsey (e.g. `0`, `null`, `undefined`, etc.), it will be `false`, otherwise, `true`.

For example, you can test IE version using this expression as below,

```js
let isIE11 = false;
isIE11 = !!navigator.userAgent.match(/Trident.*rv[ :]*11\./);
console.log(isIE11); // returns true or false
```

If you do not use this expression then it returns the original value.

```js
console.log(navigator.userAgent.match(/Trident.*rv[ :]*11\./));  // returns either an Array or null
```

*Note: The expression !! is not an operator, but it is just twice of ! operator*.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***In JavaScript, what is the difference between `var x = 1` and `x = 1`?***

`var x = 1`:

* Allowed in 'strict mode'.
* The var statement declares a function-scoped or globally-scoped variable, optionally initializing it to a value.
* Variables declared using var inside a { } block can be accessed from outside the block.
* Variables defined using var inside a function are not accessible (visible) from outside the function.
* Duplicate variable declarations using var will not trigger an error, even in strict mode, and the variable will not lose its value unless another assignment is performed.

```js
var x = 1;

if (x === 1) {
  var x = 2;

  console.log(x);
  // expected output: 2
}

console.log(x);
// expected output: 2
```

```js
var x = 5; // global
function someThing(y) {
  var x = 3; // local
  var z = x + y;
  console.log(z);
}
someThing(4); // 7
console.log(x); // 5
```

`x = 1`:

* Not allowed in 'strict mode'.
* Undeclared Variables like: x = 1 is accessible in: (Block scope - Function scope - Global scope)
* Outside of strict mode, however, if you assign a value to a name that has not been declared with let, const, or var, you\'ll end up creating a new global variable. It will be global no matter how deeply nested within functions and blocks your code is, which is almost certainly not what you want, is bug-prone, and is one of the best reasons for using strict mode!
* Global variables created in this accidental way are like global variables declared with var: they define properties of the global object.
* Unlike the properties defined by proper var declarations, these properties can be deleted with the delete operator.
* Not recommended.

```js
var x = 5; // global
function someThing(y) {
  x = 1; // still global!
  var z = x + y;
  console.log(z);
}
someThing(4) // 5
console.log(x) // 1
```

**Example:**

```js
{
  console.log(x + y); // NaN
  var x = 1;
  var y = 2;
}
```

```js
{
  console.log(x + y); // Uncaught ReferenceError: x is not defined
   x = 1;
   y = 2;
}
```

<br/>

|               | var x = 1 | x = 1 |
|:---:          | :---:     | :---:|
|Strict mode    | &#10004;  | &#10060; |
|Block scope    | &#10060;  | &#10004; |
|Function scope | &#10004;  | &#10004; |
|Global scope   | &#10004;  | &#10004; |
|Hoisting       | &#10004;  | &#10060; |
|Reassigning    | &#10004;  | &#10004; |

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How do you assign default values to variables?***

You can use the logical or operator `||` in an assignment expression to provide a default value. The syntax looks like as below,

```js
var a = b || c;
```

As per the above expression, variable 'a 'will get the value of 'c' only if 'b' is falsy (if is null, false, undefined, 0, empty string, or NaN), otherwise 'a' will get the value of 'b'.

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is the precedence order between local and global variables?***

A local variable takes precedence over a global variable with the same name. 

```js
var msg = "Good morning";

function greeting() {
  msg = "Good Evening";
  console.log(msg);
}
greeting();

// Output
Good Evening
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-precedence-n1ve75?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***What is variable shadowing in javascript?***

Variable shadowing occurs when a variable declared within a certain scope (decision block, method, or inner class) has the same name as a variable declared in an outer scope. This outer variable is said to be shadowed.

If there is a variable in the global scope, and you'd like to create a variable with the same name in a function. The variable in the inner scope will temporarily shadow the variable in the outer scope.

```js
var val = 10;

function Hoist(val) {
  console.log(val);
}
Hoist(20);

// Output: 
20
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-variable-shadowing-dvibcw?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***Explain `var self = this` in JavaScript?***

`self` is being used to maintain a reference to the original this even as the context is changing. It is a technique often used in event handlers (especially in closures).

`this` is a JavaScript keyword which refers to the current context. Unlike other programming languages, JavaScript does not have block scoping(in C open/close {} curly braces refers to a block). JavaScript has two scopes namely, global and local scope.

```js
// this Context
const context = {
  prop: 10,
  getCurrentContext: function () {
    return this.prop;
  }
};

console.log(context.getCurrentContext());
// expected output: 10
```

*Note: 'self' should not be used this way anymore, since modern browsers provide a global variable self pointing to the global object of either a normal window or a WebWorker.*

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-self-this-k1w0e8?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

## Q. ***How do you swap variables using Destructuring Assignment?***

```js
var x = 10, y = 20;

[x, y] = [y, x];

console.log(x); // 20
console.log(y); // 10
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-destructuring-sv99cd?file=/src/index.js)**

<div align="right">
    <b><a href="#">↥ back to top</a></b>
</div>

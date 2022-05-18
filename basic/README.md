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


**6. Arrow Function (=>):**

```js
let add = (x, y) => x + y;

console.log(add(10, 20)); // 30
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/js-arrow-function-ejlrmf?file=/src/index.js)**

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

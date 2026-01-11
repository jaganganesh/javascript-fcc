# Introduction to JavaScript
JavaScript is a versatile, high-level programming language and one of the core technologies of the World Wide Web, alongside **HTML** and **CSS**.

_JavaScript is a single-threaded language, meaning it executes one task at a time by default_. However, through mechanisms like the **Event Loop**, **callbacks**, and asynchronous programming (such as **Promises** and **Async/Await**), it can efficiently handle multiple operations—like fetching data from servers—without blocking the user interface.
# Data Types in JavaScript
JavaScript has **eight data types**, which are divided into two main groups:
- Primitive Data Types
- Non-Primitive Data Types

> Note: **NaN** is not a data type. It is a special numeric value.
## Primitive Data Type
Primitive values are stored **directly in memory** and are not stored as references.
### Numeric Type
- Number
- BigInt
### Non-Numeric Type
- String
- Boolean
- Null
- Undefined
- Symbol
#### Number
The **Number** data type represents both **integers and floating-point values**. JavaScript numbers are based on the **64-bit floating-point format (IEEE 754)**.
```js
let age = 25;
let height = 5.8;

console.log(age); // 25
console.log(height); // 5.8
```
###### Console Log
`console.log()` is used to **display output** in the console. It is mainly used for **debugging** and **checking values** while writing JavaScript code.
```js
let name = "Jagan";
console.log(name); // Jagan
```
##### Safe Limit

>The **safe limit** is the range of whole numbers that the **Number** data type can represent **accurately** (without losing precision).
>
>- **Maximum safe integer:** `Number.MAX_SAFE_INTEGER` → 9,007,199,254,740,991
>- **Minimum safe integer:** `Number.MIN_SAFE_INTEGER` → −9,007,199,254,740,991

```js
console.log(Number.MAX_SAFE_INTEGER); // 9,007,199,254,740,991
console.log(Number.MIN_SAFE_INTEGER); // −9,007,199,254,740,991
```
#### BigInt
**BigInt** is used to represent **very large whole numbers** that are **greater than the safe limit** of the Number type.
```js
let bigOne = 12345678901234567890n;
let bigTwo = BigInt("12345678901234567890");

console.log(bigOne); // 12345678901234567890
console.log(bigTwo); // 12345678901234567890
```

> Note: **BigInt** cannot contain decimal values.
#### String
The **String** data type is used to store **text**. Strings can be created using **single quotes**, **double quotes**, or _template literals_.
```js
let firstName = "Jagan";
let lastName = 'Ganesh';

console.log(firstName); // Jagan
console.log(lastName); // Ganesh
```
##### Template literals
Template literals allow you to _embed variables, expressions, and multi-line text_ inside strings.
```js
let name = "Jagan";
let age = 32;

let message = `My name is ${name} and I am ${age} years old.`;
console.log(message);
```
##### String literals
Individual characters inside a string are called string literals.
##### Find Length of a String
You can find the **number of characters** in a string using the **`.length`** property.
```js
let city = "Chennai";
console.log(city.length); // 7
```
##### Bracket Notation in Strings
Bracket notation allows you to **access individual characters** in a string using their **index**.
```js
// Access First Character
let name = "John";
console.log(name[0]); // "J"

// Access Last Character
let name = "Mike";
console.log(name[name.length - 1]); // "e"
```
##### String Immutability
_Strings are immutable in JavaScript_, which means **once a string is created, you cannot change its individual characters directly**. If you want a different string, you have to **create a new string**.
```js
let lastName = "Doe";

// Trying to change a character does NOT work
lastName[0] = "J";
console.log(lastName); // "Doe" (remains unchanged)

// Creating a new string works
lastName = "Joe";
console.log(lastName); // "Joe"
```
##### Concatenate Strings
Strings can be concatenated using **arithmetic operators**, **compound assignment**, or **template literals**.
###### Escape Sequence in Strings
Escape sequences are used to represent **special characters** inside strings.
```
\' → single quote
\" → double quote
\\ → backslash
\n → new line
\t → tab
\r → carriage return (moves the cursor to the beginning of the line; originally used in typewriters)
\b → backspace
\f → form feed (originally used to advance to the next page in printing; now rarely used and implementation-dependent)
```
#### Boolean
A **Boolean** data type has only two possible values:
- **`true`**
- **`false`**
```js
let isLoggedIn = true;
let hasAdminAccess = false;

console.log(isLoggedIn); // true
console.log(hasAdminAccess); // false
```
#### Null
`null` is a data type that represents **no value** or **empty**. It is used when you want to **explicitly indicate that a variable has no value**.
```js
let currentUser = null;

console.log(currentUser); // null
console.log(typeof currentUser); // object (this is a known JavaScript quirk)
```
#### Undefined
`undefined` is a data type that represents a variable that has **been declared but has not been assigned a value**. It basically means _no value yet_.
```js
let name;

console.log(name);        // undefined
console.log(typeof name); // undefined
```

> **Null → "Nothing here, I put it intentionally"**
> Think of an **empty box** you placed on purpose.

> **Undefined → "I forgot to put something here"**
> Think of a **box that exists but you never filled**.
#### Symbol
Symbol is a **unique and immutable** primitive data type. Symbols are mainly used as **unique identifiers** for object properties, ensuring that property keys do not conflict with others.
```js
let id1 = Symbol("id");
let id2 = Symbol("id");

console.log(id1 === id2); // false (each Symbol is unique)
```

> Note: Symbols are perfect when you need **unique, collision-free identifiers** — for object keys, constants, or customizing behavior with well-known symbols.
###### Example
```js
// Create unique symbols for different roles
const admin = Symbol("role");
const editor = Symbol("role");

let user = {};
user[admin] = "Alice";
user[editor] = "Bob";

console.log(user[admin]);  // Alice
console.log(user[editor]); // Bob
console.log(admin === editor); // false (each Symbol is unique)
```

> Even though both symbols have the same description "role", they are **unique identifiers**.
## Non-Primitive Data Type
Non-Primitive data types, also known as _reference types_ or _object types_, are used to store collections of data and more complex entities.

> Note: Unlike primitive types (which store the actual value), non-primitive variables store a reference to the location of the object in memory.
### Objects
All non-primitive values in JavaScript are objects.
- Object
- Date
- RegExp
- Array
- Function
#### Object
It is used to store data in the form of key–value pairs.
```js
let user = {
  name: "Jagan",
  age: 25,
  isActive: true
};

console.log(user.name); // Jagan
console.log(user.age);  // 25
```

> Note: Objects are **mutable**, which means their values can be changed.
#### Array
Array values are stored in an ordered list, and each value has an index number (starting from 0).
```js
let fruits = ["Apple", "Banana", "Orange"];

console.log(fruits[0]); // Apple
console.log(fruits[2]); // Orange
```
##### Find Length of an Array
```js
console.log(fruits.length); // 3
```

> Note: Arrays are **mutable**, meaning elements can be added, removed, or changed.
#### Function
A function performs a specific task and runs only when it is called.
```js
const greet = (name) => {
  console.log("Hello " + name);
};

greet("Jagan"); // Hello Jagan
```
##### Passing values to a Function with Arguments
```js
const myFunc = (isActive) => {
	console.log('Argument: ' + isActive);
};
```
##### Function with Return Value
```js
const add = (a, b) => {
    return a + b;
};

console.log(add(5, 10)); // 15
```

> Note: If a function does not explicitly return a value, it automatically returns `undefined`.
#### Date
The **Date** object is used to work with **dates and times** in JavaScript. It allows you to create, read, and manipulate dates such as the _current date, specific dates, and time values_.
```js
let today = new Date();

console.log(today); // current date and time
```
##### Get Date Components
```js
let now = new Date();

console.log(now.getFullYear()); // Year
console.log(now.getMonth());    // Month (0–11)
console.log(now.getDate());     // Day of the month
console.log(now.getHours());    // Hours
console.log(now.getMinutes());  // Minutes
```

> Note: The **Date object is mutable**, meaning its values can be changed using setter methods like `setFullYear()`, `setMonth()`, etc.
#### RegExp
The **RegExp** (Regular Expression) is used to search, match, and manipulate patterns in strings. It is especially useful for validation, searching, and text replacement.
```js
let pattern = /hello/;
let text = "hello world";

console.log(pattern.test(text)); // true
```
---
# Variables
Variables are containers used for storing data values. Modern **JavaScript (ES6+)** primarily uses `let` and `const`. The `var` keyword is older and generally discouraged due to scoping issues.
## Declaring Variables
A variable declaration creates a **named memory space** that can store a value. You can declare a variable and optionally assign a value to it at the same time.
```js
let name; // undefined
```

> Note: Variables are **case-sensitive**, and most developers prefer **camelCase** for naming variables.
## Assigning Variables
You can assign a value to a variable using the **assignment operator ` = `**.
```js
let name = "Jagan"; // Jagan
```
### var
`var` is the **oldest way** to declare variables in JavaScript. It has **function scope** and can be **re-declared and reassigned**, which may lead to unexpected behavior.
```js
var city = "Chennai";
var city = "Bangalore"; // allowed

console.log(city); // Bangalore
```

> Note: `var` is generally discouraged in modern JavaScript due to **scoping and hoisting issues**.
### let
`let` was introduced in **ES6** and is **block-scoped**. It allows **reassignment** but does **not allow redeclaration in the same scope**.
```js
let age = 25;
age = 26; // allowed

console.log(age); // 26
```
### const
`const` is also **block-scoped** and is used to declare variables whose values **should not be reassigned**. A value must be assigned at the time of declaration.
```js
const country = "India";

/*
country = "Singapore"; // Not allowed
*/

console.log(country); // India
```

> Note: `const` does **not** make objects or arrays immutable — only the **reference** is constant.
# Hoisting
Hoisting is a JavaScript behavior where variable and function declarations are processed before code execution.
## Variable Hoisting
The behavior of hoisting depends on **how the variable is declared**.
### `var` Hoisting
Variables declared with `var` are hoisted and initialized with `undefined`.
```js
console.log(a); // undefined
var a = 10;
```
### `let` and `const` Hoisting
Variables declared with `let` and `const` are hoisted but not initialized. Accessing them before declaration results in an error due to the **Temporal Dead Zone (TDZ)**.
```js
console.log(b); // ReferenceError
let b = 20;
```

> Note: The **Temporal Dead Zone** is the time between entering a scope and declaring the variable, during which the variable cannot be accessed.
## Function Hoisting
### Function Declaration
Function declarations are **fully hoisted**, meaning they can be called before they are defined.
```js
greet();

function greet() {
  console.log("Hola!");
}
```
### Function Expression
Function expressions are **not hoisted** the same way. If assigned to `var`, only the variable is hoisted.
```js
sayHi(); // TypeError

var sayHi = function () {
  console.log("Hi");
};
```
### Problems Caused by Hoisting
- Accessing variables before declaration can cause **unexpected bugs**
- `var` hoisting can silently return `undefined`
- `let` and `const` can throw **ReferenceError** due to TDZ
- Function expressions may cause **TypeError** if called early
### Solutions and Best Practices
- Always **declare variables at the top of their scope**
- Prefer `let` and `const` over `var`
- Avoid using variables before they are declared
- Use **function declarations** when hoisting behavior is required
> Note: Understanding hoisting helps you **write predictable code** and **avoid runtime errors**, especially when working with larger codebases.
# Scopes
==Scope determines where variables can be accessed or used in a JavaScript program==. It defines the **visibility and lifetime** of variables and functions.

In JavaScript, scope controls **where a variable is available** and **where it is not**.
.
## Global Scope
Variables declared **outside of any function or block** are in the global scope. They can be accessed **from anywhere** in the program.
```js
let myGlobal = 10; // Global variable

const myFunc = () => {
  oopsGlobal = 5; // Not using var, let, or const makes the variable global
}

const myFuncTwo = () => {
  let myOutput = '';

  if (typeof myGlobal !== 'undefined') {
    myOutput += `myGlobal: ${myGlobal}\n`; // myGlobal: 10
  }

  if (typeof oopsGlobal !== 'undefined') {
    myOutput += `oopsGlobal: ${oopsGlobal}`; // oopsGlobal: 5
  }

  console.log(myOutput);
}

myFunc();
myFuncTwo();
```

> Note: In **strict mode**, assigning a variable without `var`, `let`, or `const` throws an error.
### Strict mode
> **Strict mode** helps you catch common coding mistakes and unsafe actions **early** by turning them into errors. You can enable strict mode by adding `"use strict"` at the **top of a JavaScript file** or at the **beginning of a function**.
## Function Scope
Variables declared inside a function are **function-scoped** and can only be accessed **within that function**.
```js
const myFunc = () => {
	var myVar = 5;
	console.log(myVar); // 5
}

console.log(myVar); // ReferenceError: myVar is not defined
```

> Note: Variables declared with `var` follow **function scope**, not block scope.
## Block Scope
Variables declared using **let** and **const** inside a block `{}` are **block-scoped**. They are only accessible within that block.
```js
if (true) {
  let age = 25;
  console.log(age); // 25
}

console.log(age); // ReferenceError
```
## Lexical Scope
==Lexical scope means that inner functions can access variables from their outer scope==. Scope is determined by **where the code is written**, not where it is executed.
```js
const outer = () => {
  let count = 10;

  function inner() {
    console.log(count);
  }

  inner();
}

outer(); // 10
```
## Global vs Local Scope
When the same variable name is used in both **global** and **local** scope, the **local scope variable takes precedence over the global variable**.
```js
let value = 10;

if (true) {
  let value = 20; // Takes precedence over global scope
  console.log(value); // 20
}

console.log(value); // 10
```
# Operators
Operators are symbols used to **perform operations on values and variables**. They are commonly used for **calculations, comparisons, and assignments** in JavaScript.

> Note: JavaScript also supports **comparison**, **logical**, and **ternary** operators, which are covered in later sections.
## Arithmetic Operators
Arithmetic operators are used to perform **mathematical operations**.
```js
let a = 10;
let b = 5;

console.log(a + b); // 15
console.log(a - b); // 5
console.log(a * b); // 50
console.log(a / b); // 2
```
## Assignment Operator
The assignment operator ` = ` is used to **assign a value** to a variable.
```js
let count = 10; // 10
```
## Compound Assignment
Compound assignment operators combine an **arithmetic operation** with **assignment**. They provide a **shorter and cleaner** way to update variable values.
```js
let score = 10;

score += 5; // same as score = score + 5
score -= 2; // same as score = score - 2
score *= 3; // same as score = score * 3
score /= 2; // same as score = score / 2

console.log(score); // 19.5
```

> Note: Compound assignment operators improve **code readability** and help reduce repetitive code.
## typeof Operator
`typeof` is used to **check the data type** of a value or variable. It is mainly used for **type checking** and **debugging** while writing JavaScript code.
```js
let name = "Jagan";
let age = 25;

console.log(typeof name); // string
console.log(typeof age);  // number
```

> Note: `typeof` always returns a **string** representing the data type (for example: `"string"`, `"number"`, `"boolean"`).
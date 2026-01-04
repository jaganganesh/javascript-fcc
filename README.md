# Introduction to JavaScript
JavaScript is a versatile, high-level programming language and one of the core technologies of the World Wide Web, alongside HTML and CSS.

_JavaScript is a single-threaded language, meaning it executes one task at a time._ However, through mechanisms like the **Event Loop**, **callbacks**, and asynchronous programming (such as **Promises** and **Async/Await**, it can efficiently handle multiple operations like fetching data from servers without blocking the user interface.
# Data Types in JavaScript
JavaScript has eight data types that are divided into two main groups.
- Primitive Data Type
- Non Primitive Data Type
> Note: **NaN** is not a data type. It is a special numeric value.
## Primitive Data Type
Primitive values are stored directly in the memory location associated with the variable, not as references to another memory location.
### Numeric Type
- Number
- BigInt
### Non Numeric Type
- String
- Boolean
- Null
- Undefined
- Symbol
#### Number
Number data type represents both **integers and floating-point values**. JavaScript numbers are based on the **64-bit floating-point format (IEEE 754)**.
```js
let age = 25;
let height = 5.8;

console.log(age); // 25
console.log(height); // 5.8
```
##### Safe Limit
>The **safe limit** is the range of whole numbers that the **Number** data type can represent **accurately** (without losing precision).
>- **Maximum safe integer:** `Number.MAX_SAFE_INTEGER` → 9,007,199,254,740,991
>- **Minimum safe integer:** `Number.MIN_SAFE_INTEGER` → −9,007,199,254,740,991
```js
console.log(Number.MAX_SAFE_INTEGER); // 9,007,199,254,740,991
console.log(Number.MIN_SAFE_INTEGER); // −9,007,199,254,740,991
```
#### BigInt
BigInt is a JavaScript data type used to represent **very large whole numbers** that are **bigger than the Safe Limit**.
```js
let bigOne = 12345678901234567890n;
let bigTwo = BigInt("12345678901234567890");

console.log(bigOne); // 12345678901234567890
console.log(bigTwo); // 12345678901234567890
```
> Note: **BigInt** cannot contain decimal values
#### String
String is used to store **text** in JavaScript. It can include letters, numbers, symbols, and spaces. You can create strings using single quotes, double quotes, or _template literals_.
```js
let firstName = "Jagan";
let lastName = 'Ganesh';

console.log(firstName); // Jagan
console.log(lastName); // Ganesh
```
##### Template literals
Template literals are a modern way to create strings in JavaScript. They make it easier to _embed variables, expressions, and multi-line text_ inside strings.
```js
let name = "Jagan";
let age = 32;

let message = `My name is ${name} and I am ${age} years old.`;
console.log(message);
```
##### String literals
Characters in a string are called String Literals.
##### Find Length of a String
You can find the **number of characters** in a string using the **.length** property.
```js
let city = "Chennai";

console.log(city.length); // 7
```
##### Bracket Notation in Strings
Bracket Notation lets you **access individual characters of a string** using their **index**.
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
Strings can be concatenated using **Arithmetic Operators**, **Compound Assignment**, or by combining **Variables**.
#### Boolean
A **Boolean** data type has only two possible values:
- true
- false
```js
let isLoggedIn = true;
let hasAdminAccess = false;

console.log(isLoggedIn) // true
console.log(hasAdminAccess) // false
```
#### Null
null is a data type that represents **no value** or **empty**. It is used when you want to **explicitly indicate that a variable has no value**.
```js
let currentUser = null;

console.log(currentUser); // null
console.log(typeof currentUser); // object (this is a known JavaScript quirk)
```
#### Undefined
undefined is a data type that represents a variable that has **been declared but has not been assigned a value**. It basically means _no value yet_.
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
> Note: Symbols are perfect when you need **unique, collision-free identifiers** - for object keys, constants, or customizing behavior with well-known symbols.
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
}

greet("Jagan"); // Hello Jagan
```
##### Function with Return Value
```js
const add = (a, b) => {
    return a + b;
}

console.log(add(5, 10)); // 15
```
#### Date
The Date object is used to work with **dates and times** in JavaScript. It allows you to create, read, and manipulate dates such as the _current date, specific dates, and time values_.
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
RegExp (Regular Expression) is used to search, match, and manipulate patterns in strings. It is especially useful for validation, searching, and text replacement.
```js
let pattern = /hello/;
let text = "hello world";

console.log(pattern.test(text)); // true
```
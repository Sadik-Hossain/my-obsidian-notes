---
author: mosh
---

Variables are Containers for Storing Data.

we use a variable to store data temporarily in the memory of a computer. We can name that variable, so that we can use it later.

In JavaScript Variables can be declared in 3 ways:
- using `var` keyword
- using `let` keyword
- using `const` keyword

for ex:\
using let keyword to declare a variable, and we give that variable a name or an identifier.

```js
let age;
console.log(age); //undefined
```


>[!tip] by default, the variable we defined in js, their value is undefined if not assigned any.


we can initialize a variable using the assignment "=" operator.

```js
let name = 'mosh' // initialized with a string value mosh
console.log(name)
```

> *string is sequence of characters.*


rules for naming variables:
- cannot be a reserved keyword (if, for, do etc)
- should be meaningful
- cannot start with a number (1name :LiCross: ) 
- cannot contain a space or hyphen
- variable names are case-sensitive meaning, `Age` and `age` are completely different.

if you wanna declare multiple variables, there are 2 ways to do this:
- declare them in one line, and separate them using commas
- initialize with a value using assignment operator

```js
let age1; age2
let fName = 'mosh'; lName = "sadik"
```

**its advised to declare separately**

```js
let name = "asd";
let age = 12;
```

## Constant

the value (primitive data types) of variable cant be changed, using `const` keyword.

if we `re-assign` value to that constant variable, we get an `Uncaught TypeError: Assignment to a constant variable.`


```js
const rate = 0.3;
rate = 1; 
console.log(rate)
```

so, if you have to reassign use `let`, otherwise use `const`.


## Data Types

**what are the kind of values that we can assign to a variable?**

in Js, we have 2 categories of types:
- primitives / value types
	- string
	- number
	- boolean
	- undefined
	- null
	- symbol (es6)
	- bigInt
- non-primitives / reference types
	- object
	- array
	- function

```js
let name = 'sadik' //string literal
let age = 22 // number literal
let isAdmin = true // boolean literal
let fname; // undefined by default
let lName = undefined // we can also explicitly initialize with undefined, but its uncommon

// instead we use null, to represent no value, we explicitly say null in order to indication no value or clear the value of a variable
let mName = null

// for example, if we ask user to choose a color, and user selects none, we value with null
let color = null
```

### Dynamic types

we have two types of programming languages.
- statically typed
- dynamically typed

in static type languages,\
when we declare a variable, the type of the variable is set & it cannot be changed in the future.

in dynamic type languages like JS,\
the type of a variable can change at run time.

>[!tldr]- compile time vs runtime
Compile time refers to the phase when the source code is translated into machine readable code (e.g., bytecode or executable) **before the program is executed**. 
>
>Any errors or issues related to the code's syntax, structure, or type compatibility
>are caught during this phase.
>
>runtime refers to the phase when the **compiled program is actually executed**, and any errors or issues related to the program's logic, data, or external  factors (e.g., file access, network connectivity) are encountered. 
>
>***Compile-time errors prevent the program from running,\
>while runtime errors occur during the program's execution.***


```js
let a = undefined;
let b = null;
let name = 'sadiq';

typeof name // "string"

name = 12
typeof name // "number" 
// typeof operator returns a string showing the data type of the operand

typeof a; // "undefined" (value along with typesis undefined)
typeof b; // "object"
```



## Object

In JavaScript,\
**an object is a collection of key-value pairs**\
where the keys are strings (or symbols), and the values can be of any data type, including other objects, arrays, or functions.

```js
let person = { //object literal syntax
name: "sadik",
age:22
}
```

keys are also known as property.

**now if wanna access a property, we can do this in 2 ways:**
- dot notation
- bracket notation

```js
person.name = "sadiq" // write
console.log(person.name) // read

// bracket notation (inside the bracket the name of the target property)
person["name"] = "hossain";
console.log(person["name"])
```

**Bracket notation use cases**

sometime, we may not know the name of the target property until the runtime. for ex:

the user might be selecting the target property,\
in the time of writing code we might not know the property we're going to access, that is going to selected at run time by user.

so, we might have another variable somewhere else like selection, that determines the name of the target property

```js
let selection = "smth" // from user (value changes at runtime)

person[selection] // this way we can acess the property in a dynamic way
```

## Array

def 1:\
**An array is an ordered collection/list of data.**\
(data can either primitive or non-primitive).\
Arrays are used to store multiple values under a single variable name.

def 2:\
**An array is a data structure that we use to represent a list of items.**

```js 
let colors = ["red","blue"] // array literals
console.log(colors) 
```

**To access an array we use index**

```js
colors[0] // specify the index, in the bracket
```

In js, arrays are dynamic, the length of an array can change. Also, it can store different data types

```js
colors[2] = "green" // added another color, increased the length of the array
```

**in js, arrays are objects.**

```js
typeof colors; // "object"
colors.pop/push... // we see a lot properties of the array using dot notation, which are inherited.

colors.length // 3 (returns the length of an array)
```

## Functions

def1:\
**A functions is basically a set of statements, that performs a task or calculates a value.**

def2:\
**A function is a block of code designed to perform a particular task.** function is executed when "something" invokes it (calls it).

key terms:\
reusable block of code, set of instructions, chunk of codes 

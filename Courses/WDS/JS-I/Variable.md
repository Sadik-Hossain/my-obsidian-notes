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
**A functions is a set of statements, that performs a task or calculates a value.**

def2:\
**A function is a block of code designed to perform a particular task.** function is executed when "something" invokes it (calls it).

key terms:\
reusable block of code, set of instructions, chunk of codes 

```js
function greet(){
// body of fn
console.log("hello!");
}

greet();
```


our function can have inputs (parameters) & this input can change how the function behaves, instead of displaying "hello world", we display "hello jhon"

```js
            //parameter -> placeholder
function greet(name){
// name is accessible in the function, not outside the fn
console.log("hello " + name);
}

greet("jhon"); // jhon here is an argument -> value
```

the function can have multiple parameters, if we don't pass all the parameter, we will get undefined. as we know, by default all the variable is initialized with the value undefined.

```js
function greet(name,lName){
console.log("hello " + name + lName);
}

greet("jhon"); // "hello jhon undefined"

```


### Types of functions

```js
//performing a task
function greet(a,b){
console.log(a,b)
}

//calculate a value
function square(num){
return num*num; // return the value to whoever is calling the function
}

square(2); // returns a value, we can use this value to initialize a variable

let res = square(2);
console.log(res); // 4
//or,

console.log(square(2));
```



## Operators

In js, we have different kinds of operators, we use this operator along with our variables & constants to create expression.

> [!tldr]- Statement vs expression
> **Statement**:\
> A statement is a complete instruction or command that does something. *It performs an action or operation in a program.* Statements *do not produce a value* on their own.
> 
> **Expression**:\
> An expression is a combination of values, variables, operators, and function calls that produce a new value. 
> *Expressions evaluate to a result or value.*
> 
> The key difference is:
> - Statements perform actions or operations. 
> - Expressions produce values or results.
> 
> Statements can contain expressions, but expressions alone do not perform any action. For example, `let x = 5 + 3;` is a statement that contains the expression `5 + 3 `, which evaluates to `8` and assigns that value to the `variable x` . 
> 
> In summary, statements do things, while expressions produce values.

different kinds of operators:
- arithmetic
- assignment
- comparison
- logical
- bitwise

### arithmetic 

used for performing calculation.

```js
(x + y)
(x - y)
(x * y)
(x / y)
(x % y)
(x ** y) // exponential x to the power of y
```

```js
let x = 10;

// increment (++)
console.log(++x); // 11, before x, the value will be incremented by 1 first, then we will see that console.

console.log(x++); // 10, after x, we will x on the console first, and then the value will be incremented

console.log(x); // 11


// decrement (--)
--x // decrement first then display
x-- // display first then decrement
```


### Assignment 

used to assign a value.

```js
let x = 10;
x++; // equivalent to, x = x + 1;
x+= 5 // x = x + 5 // adds 5 to x & assign it to x
x*= 3 // x = x * 3 // multiplies 3 to x & assign it to x
```

### comparison

used to compare the value of a variable with something else.

```js
let x = 1;

// relational operator
x > 0; //true , the result of an expression, that includes a comparison operator is a boolean.
x>= 0
x < 0
x <= 0

// equality operator
x === 1;
x !== 1;

// strict equality (ensures both operands have the same type + value)
'1' === 1; // false, as the type dont match

// loose equality (it converts the data type and then checks the value)
'1' == 1; // '1' == '1' true, converts what is on left side and converts the right side
true = 1; // true == true
```

loose equality operator doesn't care about the types matching, if the types don't match, it will convert the type of what we have on the right side to match what we have on the left side.\
and will only check if the values are equal.


### Ternary / conditional

```js
let points = 100;

let type = points > 100 ? "gold" : "silver";
// if the `points > 100` expression produces true, assign value "gold" to the type variable, otherwise, assign "silver"
```


### Logical

used for making decision based on multiple conditions.

3 types of logical operator
- and
- or
- not

```js
// Logical AND (&&)
// returns TRUE if both operands are TRUE

true && true; //true, the result of evaluating this expression will be true.

false && true; //false, if either of these is false, it will result false


// Logical OR (||)
// returns TRUE if one of the operands is TRUE

false || true; //true
true || true; //true
false || false //false

// NOT (!)
// returns the opposite boolean value of the operands boolean value

!3 // false
!true // false
!"" // true
```

If a value can be converted to `true`, the value is so-called **truthy**. If a value can be converted to `false`, the value is so-called **falsy**.

Examples of expressions that can be converted to false are:
- `null`;
- `NaN`;
- `0, -0, 0n`;
- empty string (`""` or `''` or ` `` `);
- `undefined`;



### Logical operators with non-Booleans

**The result of a logical expression is not necessarily a true or false. That depends on the value of the operands we have.**


```js
false || true // true;

false || "sadik" // "sadik";

false || 1 // 1

```


when our JavaScript engine, tries to evaluate this expression, it looks at each operand.\
if that operands is not a boolean true or false. It will try to interpret it as truthy or falsy.


Falsy values:
- `undefined`
- `null `
- `0`
- `false`
- `''`
- `NaN`

> `NaN` is returned when when a mathematical calculation doesn't produce a valid number.


```js
false || 1 || 2 // 1
// as soon we find an operand that is truthy, that operand is returned
// as our second operand is truthy (1), its value is returned & the evaluation stopped.
// It doesnt matter if we have million operands on the right side, they are completely ignored.

// this is called short-circuiting
```

real world ex:\
lets say, we have user choosing the color of their dress.

```js
// scenario 1: user picked a color
let userColor = "red";
let defaultColor = "blue";
let currentColor = userColor || defaultColor; // "red"

//scenario 2: user didnt pick any color
let userColor = undefined
let defaultColor = "blue"
let currentColor = userColor || defaultColor; // "blue"

```

### Bitwise operator

**similar to logical operators, but they work individual bits of number**

computers stored information on binary format.

```js
// 1 = 00000001 
// here we have 8digits/bits,which represents 1byte of info

// 2 = 00000010

//bitwise OR
console.log(1 | 2); // 3

// if either of this bits is one, the result will be one, otherwise 0
// 1 = 00000001 
// 2 = 00000010
// R = 00000011 (result which in decimal 3)


//bitwise AND
console.log(1 & 2); // 0

// if both numbers are 1, the result will be one, otherwise 0
// 1 = 00000001 
// 2 = 00000010
// R = 00000000 (result which in decimal 0)
```


real-world ex:

imagine an user can have access control\
read, write, exec permission\
we can use 1 byte/8bit of info to determine the permission an user can have.

```js
// read perm
// 00000100

// write perm
// 0000010

// exec perm
// 0000001

// read, write, exec
// 00000111


const readPerm = 4; // dec conversion of bin
const writePerm = 2
const execPerm = 1

let myPerm = 0;
myPerm = myPerm | readPerm | writePerm

console.log(myPerm) // 6 , we dont care

let msg = (myPerm & readPerm) ? "yes" : "no" // "yes"

myPerm = myPerm | writePerm
 msg = (myPerm & readPerm) ? "yes" : "no" // "no"


// with the bitwise OR operator, we can add perm
// with the bitwise AND operator, we can check to see if we have the given perm

```


### operators precedence 

BODMAS

```js
let x = 2 + 3 * 4 // 14

let x = (2 + 3) * 4 // 20
```















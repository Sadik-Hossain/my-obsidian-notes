---
author: mosh
---

## Cond. Statements

in Js, we have 2 types of cond. statements:
- if ... else
- switch ... case
### If Else


```js
if(cond.){
statement
}
else if (cond.2){
statement
}
else if (cond.3){ // we can add as many cond. we want
statement
}
else{ // if nothing none of the above evalutes to true, this statement will get executed
statement
}

// if the cond. evalutes to true, then the statement after will executed
// if we have multiple statement, we need to put them in between curly braces. We refer this as a block of code

```


### Switch case


```js

let role;

// instead of adding a cond. here, we add a variable

switch(role){ 

// now we add 1 or more case statement, each case statement is used to compare the value of this variable with something.
case 'guest':{
	console.log(role)
	
	// use break or it will continue to case 2, break will jump out of the switch block
	break; 
	}
case 'admin':{
	console.log(role)
	break;
}
// default is optional, and we dont need break in default
default:
	console.log("unknown user")
}


```


## loops

sometime we want to repeat an action multiple times. For ex: repeating `hello world!` 5 times in console

**loops essentially repeats an action a number of times.**

in js, we have various kind of loops.
- for
- while
- do...while
- for...in
- for...of

### For

for loops need 3 statements
- initial statement
- condition (loop will run as long as the cond. is true)
- increment expression
```js

for(initialExpression; condition;increment expression ){
	statement
}

for (let i = 0; i < 5; i++){
console.log('hello', i);
}

// step 1: i = 0
// step 2: cond. evaluated to true
// step 3: executes the statement, 1st iteration complete
// step 4: incremented i
// step 5: cond. evaluated to true
// step 6: executes the statement, 2st iteration complete
// step 7: incremented i
...

// at first iteration, i = 0; at fifth iteration i = 4

for (let i = 1; i <= 5 ; i++){
	if (i%2 !== 0){
		console.log(i) // 1, 3, 5
	}
}

for (let i = 5; i >= 1 ; i--){
	if (i%2 === 0){
		console.log(i) // 4, 2
	}
}
```


### While

one key difference between a while loop & a for loop is that,\
in for loop the `loop variable` is part of the loop itself.

but, in while loop we have to declare this variable externally. 
```js
let i = 0;

while (i <= 5){ //cond.
console.log(i);
i++;
}

// first the cond. is evaluated
// if true then excute the block
// in the next iteration cond. evaluated
// if true execute otherwise terminate
``` 

### Do...while

just like while loop, we have declare our loop variable externally.

**Do while loop is *always executed once*, even if the cond. evaluates to false**

```js
let i = 9;

do{
console.log(i); // prints 9
i++;
} while(i<=5); // cond. is evaluated at the end. the statements always executed once. Even if the condition is false.

```


### Infinite loop

```js

let i = 0 ;
while (i < 5) {
console.log(i); 
//this will create an infinite loop, as we didnt increment, and the cond. always evaluates to true.
}

while (true){
statement // no increment/dec
}

do {
statement // no increment/dec
} while (true) 

for (let i = 0; i > 0; i++){ //cond. always evaluates true
statement
}
```


### For..in

**we use for...in loop for iterating over an objects properties.**


```js
const person = {
name: "sadik",
age: 22,
isAdmin: true,
}

// this key variable in the loop, will hold the name of one of the properties in this person object

for (let key in person){
console.log(key) // name age isAdmin
}

for (let key in person){

// this wont work, because we dont have a property called key in the person object
console.log(person.key) 

//or,
console.log(person[key]) // "sadik" 22 true
}

```

using for...in  to iterate over array

```js
const col = [100,122,223]

for (let index in col){
console.log(index); // 0, 1, 2
console.log(col[index]) // 100,122,223
}

```

### For...of

for...of is used to iterate over arrays.\
with for of loop, we dont have to deal with this index, we dont have to access the element.

```js
let colors = ["r","g","b"];

// in each iteration, the color variable will hold one of the items in the array

for (let color of colors){
console.log(color)
}

```



### Break & Continue

***break* & *continue* can change how the loop behaves.**

You can use `break` and `continue` in loops to alter the flow of the loop.

`break` will stop the loop from continuing, and `continue` will skip the current iteration and continue the loop.

- `break` is used to jump out of loop
- The `continue` statement terminates execution of the statements in the current iteration of the current loop, and continues execution of the loop with the next iteration

```js

let i = 0;
while(i <=10){

  if(i===5){ // if this cond. is true, jump out of the loop
	break;
	}
	console.log(i);
	i++;
}

// result: 0,1,2,3,4
```

```js
let text = '';

for (let i = 0; i < 10; i++) {
  if (i === 3) {
    continue;
  }
  text = text + i;
}

console.log(text);
// Expected output: "012456789"
```

## Exercise

**1.**\
write a func. that takes 2 numbers and returns the maximum of the two.

```js
function max (a,b){
let c;
if (a>=b){
c = a
}
if(a<b){
c = b
}
return c;
}

// mosh

function max(a,b){
if(a > b) return a;
// else return b
return b;
// return (a > b) ? a : b
}
```

**2.**\
Landscape or portrait

```js
function isLandscape (w,h){
// return (w > h) ? true : false
return (w > h )
}
```

**3.**\
FizzBuzz - number divisible by 3 => fizz, by 5 => buzz, 3 & 5 => fizzBuzz 

```js
function fizzBuzz(n){

if( typeof n!== "number"){
// return "not a number";
 return NaN; // typeof NaN -> "number"
}

if (n%3 === 0 && n%5 === 0) {
return "fizzBuzz";
};

if (n%3 === 0){
	return "fizz";
};

if (n%5 === 0){
	return "buzz";
};
return n;
}
```


%% hoisting is the process of moving function declarations to the top of the file. This is done automatically by JS. %%

**4.**\
lets say, we have a speed limit of 70kmph, if a car driving under or equal to the speed limit, we get "ok" in the console.\
now every 5 km above the speed limit will get 1 point, if you drive 75kmph, you get `point: 1` in the console.

case:\
now if u drive 72kmph, ur still get "ok", so every 5km above the speed limit, u will get 1point. 

==hint:==\
u will have to use `Math.floor()` fn, it converts floating point number to the greatest integer. ex: `Math.floor(1.3) // 1 `

if u drive 80kmph, u will get  `point: 2`. if u drive 180kmph, u get `license is suspended` as u get more than `point: 12` u get this message.

```js
function chkspd(n){

if(n<=70){
return "ok"
}
n%5
}
```
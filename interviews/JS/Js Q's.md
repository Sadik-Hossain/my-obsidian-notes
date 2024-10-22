---
tag: 
 - js
 - interview
source:
 - roadmap.sh
---


> [!tldr]- What is the difference between **null** and **undefined**?
> variation 1:\
>  The **null** is an *assignment value*. It can be assigned to a variable ==as a representation of no value.== 
> 
> But the **undefined** is a *primitive value* that ==represents the absence of a value, or a variable that has not been assigned a value.==
> 
> variation 2:\
> In JavaScript, “undefined” is the default value new variables take, and it means the variable has been defined, but it hasn’t been assigned any value just yet.
> And “null” is actually a value that signals “no value” or “no object”, it is specifically assigned to the variable by the developer.
> 



> [!tldr]- What is the difference between  " == "   and " === "  ?
> The == equality operator converts the operands if they are not of the same type, then applies strict comparison.
> 
The === strict equality operator only considers values equal that have the same type.


> [!tldr]- What is the difference between `var`, `let`, and `const` in JavaScript?
> In JavaScript, `var` is function-scoped and was traditionally used to declare variables.
> 
> `let` and `const` are block-scoped. The key difference between `let` and `const` is that `let` allows for reassignment while `const` creates a read-only reference.


> [!tldr]- What are Scopes in JavaScript?
>  The scope is a **region of the program where a variable can be accessed.**\
>   In other words, scope **determines the accessibility/visibility of a variable.**
> 
> There are three types of scopes in JavaScript. 
> Which are:
> - Global Scope
> - Function Scope (Local Scope)
> - Block Scope.
> 


> [!tldr]- what is lexical scope?
> Lexical scope is the ability of a `function scope` to access variables from the parent scopes.\
> 


> [!tldr]- What is a closure in JavaScript?
> A closure is a function that has access to its outer function scope even after the outer function has returned.
> 
>  This means a closure can remember and access variables and arguments of its outer function even after the function has finished.
>  

```js
function outer() {
  const name = 'Roadmap';

  function inner() {
    console.log(name);
  }

  return inner;
}

const closure = outer();
closure(); // Roadmap
```

In the above example, the `inner` function has access to the `name` variable of the `outer` function even after the `outer` function has returned. Therefore, the `inner` function forms a closure.



> [!tldr]- Does Arrow functions have their own `this`  ?
> No, arrow functions do not have their own `this`. Instead, they inherit the `this` of the enclosing lexical scope.



> [!tldr] Statement vs Expression
> An expression is like expressing / producing a value / asking for a value.
> 
>   an expression 'asks' JS for a value.\
>   for ex:
>   ```js
>   myVariable // evalute / whats the value of this variable?
>   6 + 4 
>   document.getElemendById("board")
>   ```
>   A statement "tells" js to do something.\
>   (ex: declare / assign a variable)
>   ```js
>   
>   let ten = 6 + 4; // assign the value to this variable
>   myVar = "new";
>   let board =  document.getElemendById("board")
>   
>   function add(x , y){
>   console.log(x) // print this value to the console
>   // give me back this value from this function
>   return x + y
>   }
>    ```
>   

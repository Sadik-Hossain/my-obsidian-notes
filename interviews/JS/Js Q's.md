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
> A scope is a set of variables, objects, and functions that you have access to. There are three types of scopes in JavaScript. 
> Which are:
> - Global Scope
> - Function Scope (Local Scope)
> - Block Scope.
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




<div align="center"> 
  <u>" Whenever an execution context is created, a lexical environment is also created "</u> 
</div>

## Lexical Environment

Definition: A lexical environment is the local memory of a function or block of code, which stores its variables and functions, along with a reference to the lexical environment of its parent.

Let's straight away see an example demonstrating lexical environment:
```javascript
function a() {
  var b = 10;

  c();

  function c() {
    console.log(b);
  }
}

a();
console.log(b); // This will cause an error
```

In this example, we can say `function c()` is lexically inside `function a()` means `function c()` is physically inside a `function a()` and `function a()` is lexically(physically) inside a global space(scope).

### Explanation:

**Lexical Environment of Function `a`:**

- When the function `a` is called, a new lexical environment is created for it.
- Inside this environment, `b` is defined and holds the value `10`.

**Calling Function `c`:**

- The function `c` is defined inside `a`, so it has access to `a`'s lexical environment.
- When `c()` is called, it logs the value of `b`, which is `10`. This is because `c` can access `b` from its parent lexical environment (`a`).

**Global Context:**

- After calling `a()`, there is an attempt to log `b` outside of any function. Since `b` is defined within the lexical environment of `a`, it is not accessible in the global context.
- Therefore, `console.log(b);` will result in a **ReferenceError**: `b is not defined`.

### Main points that we can draw from above:

- Each function creates its own lexical environment.
- Inner functions can access variables from their parent lexical environments.
- Variables defined in a function are not accessible outside that function's lexical environment.

### Key points:
- it holds variables and functions specific to that block of code.
- it can also access variables from outer blocks(parent contexts).

******

## Scope Chain

Definition: The scope chain is the order in which JS looks for variables. It starts from the current scope and moves outward to the parent scopes until it finds the variable or reaches the global scope. 

Lets take another example to understand this:

```javascript
let globalVar = 'I am global!';

function first() {
  let firstVar = 'I am in the first function!';
  
  function second() {
    let secondVar = 'I am in the second function!';
    console.log(globalVar); // Accesses globalVar from the global scope
    console.log(firstVar);  // Accesses firstVar from first()'s Lexical Environment
  }
  
  second();
}

first();
```

In this example, The function `second()` can access the variables *firstVar* and *globalVar* because of the scope chain, which links it to the first() function’s Lexical Environment and then to the global scope.

### Key Points:

- The Scope Chain allows inner functions to access variables from their outer environments.

******



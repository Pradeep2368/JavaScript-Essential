## Understanding The Block, The Block Scope and The Shadowing in JavaScript

### What is a Block?

A **block** is a piece of code that is enclosed in curly braces `{}`. Blocks are used in various constructs in JavaScript, such as `if` statements, `for` loops, and function definitions. Blocks help in grouping statements together.

### Example of a Block

```javascript
if (true) {
  let message = "Hello, World!"; // This is a block
  console.log(message); // Accessible here
}

```



### What is Block Scope?

**Block scope** refers to the visibility and accessibility of variables defined within a block, which is a section of code enclosed by curly braces `{}`. In JavaScript, variables declared with `let` and `const` are block-scoped, meaning they can only be accessed within the block they are defined in.

### Example of Block Scope

```javascript
if (true) {
  let blockScopedVar = "I am block-scoped"; // This variable is block-scoped
  console.log(blockScopedVar); // Accessible here
}

console.log(blockScopedVar); // Error: blockScopedVar is not defined
```

Anyway, we can declare a variable using `let` and `const` in a global scope. Declaring in a global scope will make those variables be accessible anywhere in the code.
Example:
```javascript
let globalVar = "I am global"; // Global variable

if (true) {
  let blockScopedVar = "I am block-scoped"; // Block-scoped variable
  console.log(globalVar); // Accessible here
  console.log(blockScopedVar); // Accessible here
}

console.log(globalVar); // Accessible here
console.log(blockScopedVar); // Error: blockScopedVar is not defined
```

### What is Shadowing?

**Shadowing** in JS occurs when a variable declared withing a certain scope (such as a block, function, or loop) has the same name as a variable in an outer scope. The inner variable  `shadows` or `overrides` the outer variable within its own scope.

### Example of Variable Shadowing

```javascript
let outerVar = "I am outside!"; // Outer variable

function exampleFunction() {
  let outerVar = "I am inside!"; // Inner variable, shadows the outer variable
  console.log(outerVar); // Logs: "I am inside!"
}

exampleFunction();
console.log(outerVar); // Logs: "I am outside!"
```

Explanationt:
- Outer Scope: The variable outerVar is declared in the global scope.

- Inner Scope: The variable outerVar is declared again within the exampleFunction, which shadows the outer variable.

- Inside the function, the inner outerVar is logged, which outputs: "I am inside!".

- Outside the function, the outer outerVar is logged, which outputs: "I am outside!".

***








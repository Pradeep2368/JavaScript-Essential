# Scope in JS (Understanding scope is crucial for managing variable visibility and lifetime in your JavaScript programs. It helps prevent naming conflicts and unintended side effects in your code.)

### Definition:
 - The scope is the current context of execution in which values and expressions are "visible" or can be "referenced".

 - If a variable or expression is not in the current scope, it will not be available for use.

 - Scopes can ablso be layered in a hierarchy, so that child scopes have access to parent scopes, but not vice versa.

### Types of scope
- JavaScript primarily has three types of scope:
  
      1. Global Scope
      2. Function Scope
      3. Block Scope
      4. Lexical Scope


  
1. Global Scope
   - Variables declared outside of any function or block are in the global scope. They can be accessed from anywhere in your code.

Example: 
```javascript
let globalVar = "I am global"; // Global variable

function displayGlobalVar() {
  console.log(globalVar); // Accessible here
}

displayGlobalVar(); // Logs: I am global
console.log(globalVar); // Also accessible here
```

Explanation:
In the example, globalVar is defined outside any function, making it globally accessible within the entire script. Both the function displayGlobalVar and the global scope can access globalVar.



2. Function Scope
   - Variables declared inside a function are scoped to that function. They cannot be accessed from outside the function.

Example:
```javascript
function myFunction() {
  let localVar = "I am local"; // Local variable
  console.log(localVar); // Accessible here
}

myFunction(); // Logs: I am local
console.log(localVar); // Error: localVar is not defined
```

Explanation:
Here, localVar is declared inside myFunction. It can only be accessed within the function itself. Trying to access localVar outside the function results in an error.


3. Block Scope
   - Variables declared within a block (enclosed by {}) are block-scoped. They can only be accessed within that block.
  
Example:
```javascript
if (true) {
  let blockVar = "I am block-scoped"; // Block-scoped variable
  console.log(blockVar); // Accessible here
}

console.log(blockVar); // Error: blockVar is not defined
```

Explanation:
In this example, blockVar is defined within an if block. It can be accessed inside the block, but trying to access it outside results in an error.


4. Lexical scope
   - Lexical scope refers to how variable scope is determined by the physical structure of the code (where the variable is declared). In JavaScript, functions are lexically scoped.

Example:
```javascript
function outerFunction() {
  let outerVar = "I am from outer function";

  function innerFunction() {
    console.log(outerVar); // Accessible here due to lexical scope
  }

  innerFunction();
}

outerFunction(); // Logs: I am from outer function
```

Explanation:
In this example, innerFunction can access outerVar because it is defined in the outer scope, demonstrating lexical scope.

### Conclusion:
- Global Scope: Variables declared outside functions or blocks. Accessible anywhere in the code.
  
- Function Scope: Variables declared inside functions. Accessible only within that function.

- Block Scope: Variables declared within blocks (e.g., if, for). Accessible only within that block.

- Lexical Scope: The structure of the code determines variable accessibility, allowing inner functions to access variables from their outer functions.

  ***




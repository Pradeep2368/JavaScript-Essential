# Execution Context

## What is Execution Context?

An **execution context** is like a box that holds everything needed to execute a piece of code. It includes important information such as:

1. **Variable Environment**: Where all the variables and functions declared in that context are stored.
2. **Scope**: The accessibility of variables and functions.
3. **This Keyword**: Refers to the current object executing the code.

## Types of Execution Contexts

There are three main types of execution contexts:

### 1. Global Execution Context

- Created when a JavaScript program starts running.
- Holds global variables and functions.
- Only one global execution context exists in a program.

### 2. Function Execution Context

- Created every time a function is called.
- Each function gets its own execution context, allowing it to manage its variables separately from others.

### 3. Eval Execution Context (less commonly used)

- Created by using the `eval()` function, which can execute a string of JavaScript code.

## How Does It Work?

1. When JavaScript runs, it creates a global execution context first.
2. Each time a function is called, a new execution context is created for that function.
3. When the function finishes executing, its context is removed from memory.

## Visualizing Execution Context

Imagine a classroom:

- The **Global Execution Context** is the classroom itself, where all students (variables and functions) can be seen and accessed.
- Each **Function Execution Context** is like a group project; when a student (function) works on a project, they have their own materials (variables) that don’t interfere with other groups.

## Why is it Important?

Understanding execution context helps you:

- Manage variables and functions effectively.
- Avoid naming conflicts (different functions can have variables with the same name).
- Know how the `this` keyword behaves in different situations.

## In Summary:

Execution context is essential for running JavaScript code efficiently. It ensures that each function operates in its own space, preventing confusion and errors.




## Here’s a simple JavaScript program along with a unified pictorial representation that shows the execution context and call stack

# Simple JavaScript Program

## Code Example

```javascript
let globalVar = "I'm a global variable";

function outerFunction() {
    let outerVar = "I'm from the outer function";

    function innerFunction() {
        let innerVar = "I'm from the inner function";
        console.log(globalVar); // Accesses global variable
        console.log(outerVar);   // Accesses outer variable
        console.log(innerVar);   // Accesses inner variable
    }

    innerFunction();
}

outerFunction();

+-----------------------------------------------------+
|                      Call Stack                     |
+-----------------------------------------------------+
| 1. innerFunction Context                             |
|   +-------------------------------+                 |
|   | Function Context for          |                 |
|   | innerFunction()               |                 |
|   +-------------------------------+                 |
|   |  Variables:                   |                 |
|   |  - innerVar                   |                 |
|   +-------------------------------+                 |
|                                                      |
| 2. outerFunction Context                            |
|   +-------------------------------+                 |
|   | Function Context for          |                 |
|   | outerFunction()               |                 |
|   +-------------------------------+                 |
|   |  Variables:                   |                 |
|   |  - outerVar                   |                 |
|   +-------------------------------+                 |
|                                                      |
| 3. Global Context                                   |
|   +-------------------------------+                 |
|   | Global Execution Context       |                 |
|   +-------------------------------+                 |
|   |  Variables:                   |                 |
|   |  - globalVar                  |                 |
|   +-------------------------------+                 |
+-----------------------------------------------------+

## Explanation of the Program Flow

1. Global Context: 
   - Created first when the script runs, holding `globalVar` and the function `outerFunction()`.

2. Calling `outerFunction()`: 
   - A new execution context is added for `outerFunction()`, which contains `outerVar` and `innerFunction()`.

3. Calling `innerFunction()`: 
   - Inside `outerFunction()`, `innerFunction()` is called, creating its own execution context which contains `innerVar`.

4. Accessing Variables: 
   - Inside `innerFunction()`, all three variables can be accessed: `globalVar`, `outerVar`, and `innerVar`.

5. Call Stack: 
   - The call stack shows the order of execution. `innerFunction()` is at the top while it runs, and once it completes, it’s removed, returning to `outerFunction()`, which then finishes and returns to the global context.

6. Call Stack get deleted or is removed and get empty:
   - Once the program execution is completed, the call stack also get empty removing the Global Execution Context. 

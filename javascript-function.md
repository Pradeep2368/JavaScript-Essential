<div align = "center" > "In JavaScript, functions are not just tools to perform tasks; they are the architects of logic, capable of shaping code into dynamic and reusable patterns. Mastering functions means mastering the heart of the language."</div>


# JavaScript Functions Explained

## Table of Contents
1. [Function Declaration](#function-declaration)
2. [Function Statement](#function-statement)
3. [Function Expression](#function-expression)
4. [Anonymous Function](#anonymous-function)
5. [Named Function Expression](#named-function-expression)
6. [First-Class Functions](#first-class-functions)

---

## Function Declaration
A function declaration is a way to define a named function. It's hoisted, meaning it can be called before it is defined in the code.
```javascript
function myFunction() {
  console.log('This is a function declaration');
}
myFunction(); // Works even before the function is defined
```

Key Point: Hoisted to the top of their scope.

## Function Statement 
(Often synonymous with Function Declaration)
A function statement is generally treated the same as a function declaration.

Key Point: Just another name for function declaration.

## Function Expression
A function expression is when a function is assigned to a variable. It's not hoisted like a function declaration, meaning you can't use it before it's defined.
```javascript
const myFunction = function() {
  console.log('This is a function expression');
};

myFunction(); // Can only be called after its definition
```

Key Point: Not hoisted.

## Anonymous Function
An anonymous function is a function without a name. It's commonly used in function expressions or passed as an argument.
```javascript
const myFunction = function() {
  console.log('This is an anonymous function');
};
```

Key Point: No name, used in function expressions or callbacks.

##  Named Function Expression
This is a variation of a function expression where the function has a name. The name is local to the function itself and doesn't affect the surrounding scope.
```javascript
const myFunction = function namedFunction() {
  console.log('This is a named function expression');
};

myFunction(); // Works
namedFunction(); // Error, as the name is only accessible inside the function
```

Key Point: Name is local to the function and helps in recursion or debugging.

## First-Class Functions
In JavaScript, functions are treated like any other value, such as numbers or strings. This means you can:

- Pass a function as an argument to another function.

- Return a function from another function.

- Assign a function to a variable.

We also call functions "first-class citizens" (or "first-class objects") in JavaScript because they have the same capabilities as other values like numbers, strings, or objects as mentioned above. Specifically, they can be:

- Passed as arguments: Functions can be passed as arguments to other functions (called callback functions).

- Returned from functions: A function can be returned from another function, allowing functions to generate new functions dynamically.

- Assigned to variables: Just like you can assign a number or string to a variable, you can assign a function to a variable.

```javascript
function greet() {
  return "Hello!";
}

function callFunction(func) {
  console.log(func()); // It calls the function passed as an argument
}

callFunction(greet); // Pass the 'greet' function as an argument
```

Explanation:
- The greet function returns the string "Hello!".

- The callFunction function takes another function (like greet) as an argument and calls it.

- We pass greet to callFunction, and it logs "Hello!".

Key Point: Functions can be used just like any other piece of data in JavaScript.

***

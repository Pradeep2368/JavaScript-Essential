<div align="center"> 
  <span style="font-size: 50px;">
    "A reference error is just JavaScript's way of telling you, 'I can't find that variable. Are you sure it exists?'"
  </span>
  </div>

  ## Reference Error

  *Definition:* 
  - A Reference Error occurs when JS engine tries to access a variable that hasn't been declared or is out of scope or is in the [Temporal Dead Zone(TDZ)](temporal-dead-zone.md).


##### Common Causes

- Accessing Undeclared Variables: Trying to use a variable before it is declared.
  
- Misspelling Variable Names: Typos can lead to reference errors.
  
- Using Variables Outside Scope: Accessing a variable that is not available in the current scope.

- Accessing variable which is in TDZ.

Examples:  

```javascript
// Example 1: Accessing undeclared variable
console.log(x); // ReferenceError: x is not defined

// Example 2: Misspelled variable name
let y = 10;
console.log(z); // ReferenceError: z is not defined

// Example 3: Using variable outside scope
function test() {
    let a = 5;
}
console.log(a); // ReferenceError: a is not defined

// Example 4: Accessing variable which is in TDZ
console.log(a); //  ReferenceError: Cannot access 'a' before initialization
let a = 5;

```

##### Debugging Tips

- Declare Variables First: Always declare variables before using them.

- Check Variable Scope: Ensure you understand where a variable is accessible.

- Use Console Logging: Log variables before use to verify their existence and value.


*****

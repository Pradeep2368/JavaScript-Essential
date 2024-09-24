<div align="center"> "A TypeError is a reminder that data types matter—just like in life, context is everything." </div>

## Type Error

*Definition:*

- A Type Error occurs when an operation is performed on a value of an inappropriate type or when you try to use a method/property on the wrong type, resulting in an operation that is not valid.

##### Common Causes

- Calling Non-functions: Attempting to invoke a variable that isn’t a function.

- Accessing Properties of Non-objects: Trying to access properties of undefined or null.

- Mismatched Types: Performing operations on incompatible types.


Examples: 

```javascript
// Example 1: Trying to call a non-function
let obj = {
    name: "John"
};
obj(); // TypeError: obj is not a function

// Example 2: Accessing properties of undefined
let user;
console.log(user.name); // TypeError: Cannot read property 'name' of undefined

// Example 3: Mismatched types in operations
let num = 5;
let str = "10";
console.log(num + str); // This will result in '510' (string concatenation)

// Example 4: TypeError: a.toUpperCase is not a function
let a = 5;
console.log(a.toUpperCase());

```

##### Debugging Tips

- Check if variables are set: Make sure your variables are not undefined or null before using them.

- Validate Data Types: Confirm that the data types of your variables match expected types, especially when passing to functions.

- Use browser tools: Open the browser's developer tools to check error messages and track where the issue happened.

*****

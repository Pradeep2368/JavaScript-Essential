# JavaScript Hoisting

## Definition: Hoisting is a JS behavior where variables and functions declaration are moved to the top of their scope before code execution.
## This means you can use variables and functions before assigning value to them in your code. 

### For example, with variables declared using var, they are hoisted but not their values, so you get ** undefined ** if accessed before initialization. And for functions, the ** whole function ** is hoisted, so you can call them before they are written. 

## Tools to explore Hoisting:

➡️ Chrome DevTool
  - Check Sources Tab and Console
  - Use the Sources Tab to see how code executes step by step under Scope Tab
  - Check Call Stack

## Example:
```js
console.log(myVar); // Output: undefined
var myVar = 5;
console.log(myVar); // Output: 5

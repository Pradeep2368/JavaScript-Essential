
___
Prev Read: [Errors in JS](syntax-error.md)
***
<div align = "center"> "Closures are a powerful feature of JavaScript that allow functions to retain access to their lexical scope even when the function is executed outside that scope, enabling data privacy and encapsulation." </div>


## The Closures in JS

- A closure is a function that remembers and has access to its lexical scope, even when the function is executed outside of that scope.
- Simply put it as, Function along with its lexical scope bundled together forms a closures.

Example:

```javascript
function x() {
    let a = 7;
    function y() {
        console.log(a);
    }
    return y;
}

let z = x(); 
console.log(z); // Prints: f y() { console.log(a); }
z();            // Prints: 7
```
Explanation:
1. When the code runs in DevTools (Source tab) under Scope, you'll see something like this:

- Script <br>
z: `<value unavailable>`
- Global <br>
x: `f x()`
- Local <br>
a: `<value unavailable>` <br>
y: `f y()`


Explanation of values:

`<value unavailable>` appears because the DevTools no longer hold the actual value in this context at runtime.
The `y function` is still accessible because of closure, keeping the reference to a intact.

##### Execution Breakdown:



```javascript
Line 9:
console.log(z); 
// Output in console: f y() { console.log(a); }
The function y is returned from x and stored in z. The value of z is a reference to the y function.

Line 10:
z(); 
// Output: 7
The z() invocation triggers the y() function, which accesses the `variable a` from its lexical scope, printing 7.
```

##### Common Use Cases for Closures:

1. Data Privacy:

Closures can encapsulate private variables. This is useful for creating module-like patterns in JavaScript.
```javascript
function createCounter() {
    let count = 0;
    return {
        increment: function() {
            count++;
            return count;
        },
        decrement: function() {
            count--;
            return count;
        }
    };
}
const counter = createCounter();
console.log(counter.increment()); // Output: 1
console.log(counter.increment()); // Output: 2
console.log(counter.decrement()); // Output: 1
```

2. Function Factories:

Creating functions that have preset parameters.
```javascript
function multiplyBy(factor) {
    return function(x) {
        return x * factor;
    };
}
const double = multiplyBy(2);
console.log(double(5)); // Output: 10
```

3. Event Handlers:

Maintaining state in event listeners.
```javascript
function setupButton(buttonId) {
    let button = document.getElementById(buttonId);
    let clickCount = 0;
    button.addEventListener('click', function() {
        clickCount++;
        console.log(`Button clicked ${clickCount} times.`);
    });
}
setupButton('myButton');
```

##### Best Practices for Using Closures:
- Avoid Memory Leaks: Be cautious with closures that retain references to large objects. This can lead to increased memory usage.

- Keep it Simple: Use closures judiciously. Overusing them can make code harder to understand and maintain.

- Utilize for Data Encapsulation: Use closures to encapsulate private data effectively, which improves modularity.

- Test and Debug Closures: Be aware of how closures behave in different contexts, especially within loops and asynchronous functions.


****

  Next Read:  [setTimeout](setTimeout.md)
  ***

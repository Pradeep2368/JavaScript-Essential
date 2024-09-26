# setTimeout () 

<div align = "center"> "Patience in code, like in life, brings clarity—setTimeout is the pause that lets logic unfold at the right moment."</div>

## *Definition:*

- setTimeout() is a JS function that allows you to delay the execution of a piece of code for a specific amount of time. It takes two arguments: the function to execute and the delay time in milliseconds, enabling asynchronous behavior without blocking the main thread.

Example:
```javascript
  setTimeout(function () {
  console.log("Hello World!");
  }, 3000);
```
```javascript
Same Example another way of doing it:
function sayHello() {
  console.log("Hello World!");
}
setTimeout(sayHello, 3000);
```
```
This will console.log only after 3 secs. 
```

*******Important:* <br>
 <div align="center">A setTimeOut () doesn't stop other code from running. The rest of your program will continue to run during the delay. </div>

 *One more eample adding one line more on the above program*
 ```javascript
function sayHello() {
  var i = 1;
  setTimeout(() => {
    console.log(i);
  }, 3000);
  console.log("Hello World!");
}

sayHello();
```

Output:
```javascript
Hello World!    // Immediately
1                // after 3 secs
```

Description:
1. console.log("Hello World!"): this prints "Hello World!" immediately.

2. setTimeout(): delays logging the vlaue of i (which is 1) for 3 secs.

3. The function demonstrates asynchronous behavior, where "Hello World!" is looged first, followed by i (after 3 seconds).

4. You can also see that `i` log the value 1 because the `anonymous function ()` inside `setTimeout ()` forms a closure with the lexical environment (scope) of its parent `function sayHello ()` which holds the value of `i`. The variable `i` inside the `anonymous function ()` points to the reference of `i` which is present in the parent variable.


***

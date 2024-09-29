# Understanding the Event Loop: The Hidden Mechanism Behind JavaScript's Magic
<br>

```plaintext

JavaScript is often described as a single-threaded language, but it manages to handle tasks like fetching data from servers, updating the UI, and responding to user events seamlessly without blocking or freezing.
This is made possible by a magical concept: The Event Loop.

```

##### In this article, we will dive deep into how the event loop works in JavaScript, with examples to make it easy to grasp. Understanding the event loop will help you write more efficient and non-blocking code.

##### What is the Event Loop?
The event loop is a mechanism that allows JavaScript to handle asynchronous operations like API calls, timeouts, and user interactions, all while maintaining its single-threaded nature. When we say JavaScript is single-threaded, it means it has only one call stack, which processes one function at a time. But how does it handle asynchronous tasks?

*The magic lies in the combination of the call stack, callback queue, and event loop.*

##### The Call Stack:

The call stack is where JavaScript keeps track of the function it is currently executing. When a function is executed, it gets placed on top of the stack, and once it finishes running, it's taken off the stack.

To Put it in more simple word, The call stack is like a list that keeps track of what functions are running in a program. Here's a simple breakdown:

#### Stack of Tasks: 
- Think of it as a stack of plates; each function call is a plate added on top.

- Last In, First Out (LIFO): The last function you call is the first one to finish and be removed from the stack.

- Tracking Function Calls: It helps the program remember where to go back after a function finishes running.

##### Example:
If you call Function A, then Function B from within A, the call stack looks like this:

- Top: Function B

- Middle: Function A

- Bottom: Main Program

When Function B finishes, it gets removed, and the program goes back to Function A and once the Function A finishes, it gets to Main Program and get lastly once the entire program completes, the Call Stack get Empty.

Check this one more simple example:
```javascript
function greet() { 
  console.log('Hello, world!'); 
}
greet(); 
console.log('This will run next.');
```
In this case, the call stack processes the greet() function first, then removes it and moves on to the next console.log().

#### Callback Queue:

Asynchronous operations, like timers or fetching data from an API, don’t block the call stack. Instead, they get added to the callback queue. The event loop checks the queue and pushes callbacks to the call stack only when the stack is empty.

To make it simple think Callback queue as a movie theater where you buy tickets and wait for your turn to enter the theater.

##### How It Works:

- Buying Tickets: When you arrive at the theater and buy your ticket (like starting an asynchronous operation), you don’t go inside immediately. Instead, you wait outside.

- Waiting Area: After you buy your ticket, you join a line of people waiting to enter (the callback queue).

- Doorman (Event Loop): The doorman checks the line and lets one person in at a time when the theater is empty (when the call stack is clear).

- Going Inside: When it's your turn, the doorman calls you (the callback) and lets you into the theater (adds it to the call stack).

##### Example:
```javascript
console.log('Start');

setTimeout(() => {
    console.log('This runs after 2 seconds');
}, 2000);

console.log('End');
Output:
Start
End
This runs after 2 seconds
```
Here, the setTimeout() is asynchronous. It doesn’t block the main thread. Instead, the event loop will only process its callback after the call stack is empty and the specified delay has passed.

### The Event Loop in Action:

The event loop is a key feature of JavaScript that facilitates asynchronous programming, allowing the language to manage several tasks simultaneously without freezing or blocking the main thread.

##### The event loop works by constantly checking two things:

- Is the call stack empty?

- Is there any callback waiting in the queue?

If the call stack is empty and there’s a callback in the queue, the event loop pushes that callback to the stack for execution.

*Metaphorically,* The event loop is like a waiter at a restaurant who takes orders from customers and serves food when it’s ready.

##### How It Works:

- Taking Orders: When customers (your code) place their orders (events or asynchronous tasks), the waiter writes them down and moves on to serve other customers.

- Kitchen (Callback Queue): The kitchen prepares the food (executes the tasks) and when it’s ready, it gives it back to the waiter (places it in the callback queue).

- Serving Food: The waiter checks if any food is ready. If the waiter isn’t busy serving someone else, they’ll bring the food to the right customer (push the task to the call stack).

- Repeat: The waiter keeps checking for new orders and serving food until the restaurant closes (the program finishes).

*Non-Blocking: Just like the waiter doesn’t stand idle while waiting for 
food to be cooked, the event loop continuously checks for tasks in the queue 
and serves them when it can, ensuring that the program runs smoothly.*

##### Example:
Let’s consider an example that combines both synchronous and asynchronous operations to see how the event loop behaves.
```javascript
console.log('First');

setTimeout(() => {
    console.log('Second');
}, 0);

console.log('Third');

Output:

First
Third
Second
```

Isn’t it surprising? You might think 'Second' would show up before 'Third' since the timeout is set to 0 milliseconds. However, this isn’t the case: even with a 0-millisecond timer, setTimeout() is asynchronous. It is placed in the callback queue and waits until the call stack is clear. As a result, the synchronous code, such as console.log('Third'), executes first.

##### Microtasks and Macrotasks:
In JavaScript, not all tasks are equal. The event loop handles macrotasks (like setTimeout(), setInterval()) and microtasks (like promises and something we call mutation observers) slightly differently. Microtasks have higher priority than macrotasks means promises and mutation observers are push to the Call Stack ahead of setTimeout() and all that are macrotasks.

Example:
```javascript
console.log('Start');

setTimeout(() => {
    console.log('Macrotask');
}, 0);

Promise.resolve().then(() => {
    console.log('Microtask');
});

console.log('End');
Output:

Start
End
Microtask
Macrotask
```

*Here you can see that even though setTimeout() is before promise's then(), 
still then the promise’s then() callback runs before the setTimeout() 
because microtasks (promises) are processed before macrotasks (setTimeout), 
even though both are asynchronous.*

##### Understanding the event loop is key to writing efficient and responsive JavaScript code. It ensures that your code doesn’t block the user interface and handles asynchronous tasks in a seamless manner. By mastering how the event loop works, you can avoid common pitfalls like callback hell and make better use of promises and async functions.

Lastly keep in mind,

*"In essence, the event loop is what gives JavaScript its unique non-blocking behavior, allowing it to handle multiple tasks efficiently. Understanding this hidden mechanism unlocks the true power of asynchronous programming and will make you a better JavaScript developer."*

References
Call Stack - MDN

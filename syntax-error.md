## Syntax Error

  *Definition:*
  - A Syntax Error occurs when the JavaScript engine encounters code that does not conform to the rules of the JavaScript language. This typically prevents the code from executing.

##### Common Causes
- Missing Punctuation: Forgetting a comma or semicolon can lead to syntax errors.
  
- Unmatched Quotes: Using single quotes without a matching pair, or mixing quote types.
  
- Incorrect Structure: Misplacing curly braces or parentheses can cause syntax issues.
  
- Invalid Keywords: Using reserved keywords incorrectly.

Examples: 

```javascript

// Example 1: Missing closing parenthesis
function greet(name {
    console.log("Hello, " + name);
}

// Example 2: Unmatched quotes
let message = "Hello, World!;

// Example 3: Incorrect structure
if (true {
    console.log("This will cause a syntax error.");
}
```

##### Debugging Tips
- Read the Error Message: Check the console; it often indicates the line number and type of error.
  
- Check for Common Mistakes: Look for missing commas, parentheses, or curly braces.
  
- Use Linting Tools: Use tools like ESLint to identify and fix syntax errors.
  
- Simplify Your Code: Break down complex statements to isolate the error.


*****



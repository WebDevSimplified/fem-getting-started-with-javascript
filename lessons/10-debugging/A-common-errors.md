---
description: Learn to identify and fix the most common JavaScript errors that beginners encounter, including syntax errors, runtime errors, and logical mistakes.
---

# Common JavaScript Errors

Every JavaScript developer, from beginner to expert, encounters errors. Understanding the most common types of errors and how to identify them will make you a much more efficient programmer. Let's explore the main categories of errors you'll face and how to fix them.

## Types of JavaScript Errors

In JavaScript, errors generally fall into three main categories:

1. **Syntax Errors**: Mistakes in the code that prevent it from running at all.
2. **Runtime Errors**: Problems that occur while the code is running, causing it to stop.
3. **Logical Errors (Bugs)**: The code runs without crashing, but it doesn't produce the expected results.

### Syntax Errors

Syntax errors occur when your code doesn't follow JavaScript's grammar rules. These are caught by the JavaScript engine before your code runs and usually show up in your editor as a red squiggly line or in the console as an error message.'

Some common syntax errors include:

1. Missing Commas

   ```javascript
   // ❌ Missing comma in object
   const person = {
     name: "John" // Missing comma here
     age: 30
   }

   // ✅ Fixed
   const person = {
     name: "John",
     age: 30
   }
   ```

2. Mismatched Brackets, Parentheses, or Braces

   ```javascript
   // ❌ Missing closing brace
   function greet(name) {
     console.log("Hello " + name)
   // Missing }

   // ✅ Fixed
   function greet(name) {
     console.log("Hello " + name)
   }

   // ❌ Mismatched parentheses
   if (age > 18 {  // Missing closing parenthesis
     console.log("Adult")
   }

   // ✅ Fixed
   if (age > 18) {
     console.log("Adult")
   }
   ```

### Runtime Errors

Runtime errors occur when your code runs but encounters a problem during execution that causes it to stop. These errors can be harder to catch because they only appear when the specific code is executed and do not show up in your editor.

Common runtime errors include:

1. Variable Typos

   ```javascript
   // ❌ Typo in variable name
   const userName = "john123"
   console.log(username) // ReferenceError: username is not defined (typo)

   // ✅ Fixed - correct spelling
   const userName = "john123"
   console.log(userName)
   ```

2. TypeError: Cannot Read Property/Method of Undefined or Null

   ```javascript
   // ❌ Trying to access property of null/undefined
   const user = getUser() // Assume this returns null
   console.log(user.name) // TypeError: Cannot read property 'name' of null

   // ✅ Fixed - check if object exists first
   const user = getUser()
   if (user) console.log(user.name)
   ```

3. TypeError: Assignment to Constant Variable

   ```javascript
   // ❌ Trying to reassign const variable
   const age = 30
   age = 31 // TypeError: Assignment to constant variable

   // ✅ Fixed - use let for variables that change
   let age = 30
   age = 31 // Works fine
   ```

### Logical Errors

Logical errors are similar to runtime errors, but they don't cause your code to crash. Instead, they produce incorrect results or behavior. These can be the hardest to find because the code runs without throwing any errors.

1. Off-by-One Errors

   <!-- prettier-ignore -->
   ```javascript
    // ❌ Common loop mistake
    const items = ["apple", "banana", "orange"]
    for (let i = 0; i <= items.length; i++) { // <= instead of <
      console.log(items[i]) // Prints "apple", "banana", "orange", undefined
    }

    // ✅ Fixed
    const items = ["apple", "banana", "orange"]
    for (let i = 0; i < items.length; i++) {
      console.log(items[i]) // Prints "apple", "banana", "orange"
    }
    ```

2. Assignment vs. Comparison

   <!-- prettier-ignore -->
   ```javascript
    // ❌ Using assignment (=) instead of comparison (===)
    const name = "Kyle"
    if (name = "Sally") { // This assigns "Sally" to name
      console.log("Is Sally") // This will always run
    }

    // ✅ Fixed
    const name = "Kyle"
    if (name === "Sally") {
      console.log("Is Sally") // This won't run
    }
    ```

## Common DOM-Related Errors

1. Element Not Found

   ```javascript
   // ❌ Trying to use element that doesn't exist
   const button = document.querySelector(".submit-btn")
   button.addEventListener("click", handleClick) // TypeError if button is null

   // ✅ Fixed - check if element exists
   const button = document.querySelector(".submit-btn")
   if (button) {
     button.addEventListener("click", handleClick)
   } else {
     console.warn("Submit button not found")
   }
   ```

2. Script Loading Before DOM

   ```html
   <head>
     <script src="script.js"></script>
   </head>
   ```

   ```javascript
   // ❌ Script runs before HTML is loaded
   const form = document.querySelector("form")
   console.log(form) // null - form doesn't exist yet
   ```

   ```html
   <head>
     <!-- ✅ Fixed: use defer attribute -->
     <script src="script.js" defer></script>
   </head>
   ```

## How to Read Error Messages

JavaScript error messages can seem intimidating, but they contain valuable information:

### Anatomy of an Error Message

```text
TypeError: Cannot read property 'name' of null
    at getUserName (script.js:15:20)
    at main (script.js:8:5)
    at script.js:25:1
```

Breaking this down:

- **Error Type**: `TypeError` - tells you what kind of error
- **Error Message**: `Cannot read property 'name' of null` - describes what went wrong
- **Stack Trace**: Shows where the error occurred and how we got there
  - `at getUserName (script.js:15:20)` - error happened in `getUserName` function, line 15, column 20
  - `at main (script.js:8:5)` - which was called from `main` function, line 8, column 5
  - `at script.js:25:1` - which was called from the top level, line 25, column 1

With this information we know that on line 15 of `script.js`, we tried to access the `name` property of a variable that was `null`. We can then go to that line in our code and work backwards from there to find the root cause.

### Common Error Messages and What They Mean

```javascript
// "ReferenceError: variable is not defined"
// → You're using a variable that hasn't been declared

// "TypeError: Cannot read property 'X' of undefined"
// → You're trying to access a property on undefined/null

// "TypeError: X is not a function"
// → You're trying to call something that isn't a function

// "SyntaxError: Unexpected token"
// → There's a typo or missing punctuation in your code

// "RangeError: Maximum call stack size exceeded"
// → You have infinite recursion
```

## Quick Debugging Tips

1. Read the Error Message Carefully

   Don't just glance at the error - read the entire message and look at the line number.

2. Check for Typos

   Many errors are simply typos in variable names, function names, or missing punctuation.

3. Use `console.log` Strategically

   ```javascript
   function calculateTotal(items) {
     console.log("calculateTotal called with:", items) // Debug input

     let total = 0
     for (let item of items) {
       console.log("Processing item:", item) // Debug each iteration
       total += item.price
     }

     console.log("Final total:", total) // Debug output
     return total
   }
   ```

4. Comment Out Code to Isolate Issues

   If you have a complex function with errors, comment out sections to find which part is causing the problem.

5. Check the Browser Console

   Always keep your browser's developer console open when developing to catch any runtime errors.

## Practice: Fix These Errors

Try to identify and fix the errors in these code snippets:

### Exercise 1

```javascript
const users = [
  { name: "John", age: 25 }
  { name: "Jane", age: 30 },
  { name: "Bob", age: 35 }
]

for (let i = 0; i <= users.length; i++) {
  console.log(users[i].name)
}
```

### Exercise 2

```javascript
function greetUser(user) {
  if (user.name) {
    console.log("Hello " + user.name.toUppercase())
  }
}

const user = { name: "john" }
greetUser(user)
```

<details>
<summary>Solutions</summary>

### Exercise 1 Solution

<!-- prettier-ignore -->
```javascript
// Issues: Missing comma, wrong loop condition
const users = [
  { name: "John", age: 25 }, // Added missing comma
  { name: "Jane", age: 30 },
  { name: "Bob", age: 35 },
]

for (let i = 0; i < users.length; i++) { // Changed <= to <
  console.log(users[i].name)
}
```

### Exercise 2 Solution

```javascript
// Issues: Method name typo
function greetUser(user) {
  if (user.name) {
    console.log("Hello " + user.name.toUpperCase()) // Fixed typo: toUppercase → toUpperCase
  }
}

const user = { name: "john" }
greetUser(user)
```

</details>

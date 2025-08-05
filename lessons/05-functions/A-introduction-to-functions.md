---
description: Learn how to create and use functions in JavaScript to organize your code and avoid repetition.
---

# Introduction to Functions

Functions store logic to be used later in your code similar to how variables store values for later use.

## Why Do We Need Functions?

Functions help us avoid writing the same code multiple times. Let's look at an example:

```javascript
console.log("Hello")

// ... lots of other code here ...

console.log("Hello") // We're repeating ourselves!
```

If we want to change "Hello" to "Hi", we'd need to remember to update it everywhere. This is where functions come in handy.

## Creating Your First Function

Here's how to write a function in JavaScript:

```javascript
function sayHi() {
  console.log("Hi")
}
```

Let's break this down:

1. **`function`** - The keyword that tells JavaScript we're creating a function
2. **`sayHi`** - The name of our function (follows same naming rules as variables)
3. **`()`** - Parentheses for parameters (empty for now)
4. **`{}`** - Curly braces that contain the function's code

### Function Naming

Function names follow the same rules as variables:

- Start with a lowercase letter
- Use camelCase for multiple words
- Choose descriptive names

```javascript
function sayHello() {} // Good
function calculateTotal() {} // Good
function getUserAge() {} // Good
```

## Calling (Running) a Function

Creating a function doesn't run it automatically. To execute the function, you need to **call** it:

```javascript
function sayHi() {
  console.log("Hi")
}

sayHi() // This runs the function
```

You can call the same function multiple times:

```javascript
sayHi() // Prints "Hi"
sayHi() // Prints "Hi" again
```

## Functions with Parameters

Functions become more powerful when they can accept information. These inputs are called **parameters**:

```javascript
function printName(name) {
  console.log(name)
}

printName("Kyle") // Prints "Kyle"
printName("Sarah") // Prints "Sarah"
```

### Parameters vs Arguments

- **Parameters** are the names listed in the function definition - `name`
- **Arguments** are the actual values passed when calling the function - `"Kyle"`, `"Sarah"`

Technically, these mean two different things, but many people (including myself) use them interchangeably in casual conversation.

### Multiple Parameters

You can have multiple parameters separated by commas:

```javascript
function sum(a, b) {
  console.log(a + b)
}

sum(1, 2) // Prints 3
sum(5, 7) // Prints 12
```

### Using Variables as Arguments

You can pass variables to functions:

```javascript
function add(x, y) {
  console.log(x + y)
}

let num1 = 10
let num2 = 5

add(num1, num2) // Prints 15
add(3, 7) // You can also pass values directly
```

## Common Syntax Mistakes

- Missing Parentheses

  ```javascript
  // ❌ Wrong - missing parentheses
  function sayHello {
    console.log("Hello")
  }

  // ✅ Correct
  function sayHello() {
    console.log("Hello")
  }
  ```

- Missing Curly Braces

  ```javascript
  // ❌ Wrong - missing opening brace
  function sayHello()
    console.log("Hello")
  }

  // ❌ Wrong - missing closing brace
  function sayHello() {
    console.log("Hello")

  // ✅ Correct
  function sayHello() {
    console.log("Hello")
  }
  ```

- Forgetting to Call the Function

  ```javascript
  // This creates the function but doesn't run it
  function sayHello() {
    console.log("Hello")
  }

  // You need to call it:
  sayHello() // Now it runs
  ```

## Benefits of Functions

1. **Avoid Repetition** - Write logic once, use it multiple times
2. **Easy to Update** - Change logic in one place
3. **Better Organization** - Break complex problems into smaller pieces

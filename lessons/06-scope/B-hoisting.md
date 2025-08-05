---
description: Learn how JavaScript moves function declarations to the top of their scope.
---

# Hoisting

Hoisting is a JavaScript behavior where function declarations are moved to the top of their scope during compilation. This allows you to use functions before they're defined in your code.

## Normal JavaScript Execution Order

Normally, JavaScript executes code from top to bottom:

```javascript
// ✅ This works - variable defined before use
let a = 1
console.log(a) // 1
```

```javascript
// ❌ This doesn't work - variable used before definition
console.log(b) // ReferenceError: Cannot access 'b' before initialization
let b = 2
```

### Function Hoisting in Action

However, functions work differently. You can call a function **before** it's defined:

```javascript
// ✅ This works! Function is called before it's defined
console.log(sum(1, 2)) // 3

// Function defined after it's called
function sum(a, b) {
  return a + b
}
```

## How Hoisting Works

Before JavaScript runs your code, it does a preliminary scan and **moves all function declarations to the top** of their scope.

It's as if JavaScript rewrites your code like this:

```javascript
// What you write:
console.log(sum(1, 2))

function sum(a, b) {
  return a + b
}
```

```javascript
// How JavaScript sees it (conceptually):
function sum(a, b) {
  return a + b
}

console.log(sum(1, 2))
```

Functions are either hoisted to the top of the global scope or the top of their containing function scope, depending on where they are defined.

### Arrow Functions Are **NOT** Hoisted

Arrow functions behave like variables and are **not hoisted**:

```javascript
// ✅ This works with normal functions
console.log(sum(1, 2)) // 3

function sum(a, b) {
  return a + b
}
```

```javascript
// ❌ This doesn't work with arrow functions
console.log(sumArrow(1, 2)) // ReferenceError: Cannot access 'sumArrow' before initialization

const sumArrow = (a, b) => {
  return a + b
}
```

## Why Hoisting Is Useful

Hoisting allows you to organize your code more flexibly. You can place your main program logic at the top and helper functions below, improving readability:

```javascript
// Main program logic (easy to read)
processUserData()
displayResults()
cleanup()

// Helper functions (implementation details)
function processUserData() {
  console.log("Processing...")
}

function displayResults() {
  console.log("Displaying results...")
}

function cleanup() {
  console.log("Cleaning up...")
}
```

---
description: Learn the alternate arrow function syntax - a shorter way to write functions in JavaScript with some unique features.
---

# Arrow Functions

Arrow functions are an alternate way to write functions in JavaScript. They provide a shorter syntax and have some unique features that make them especially useful for certain situations.

## Converting a Normal Function to Arrow Function

Let's start with a normal function and convert it to an arrow function:

```javascript
// Normal function
function sum(a, b) {
  return a + b
}

// Arrow function
const sumArrow = (a, b) => {
  return a + b
}

console.log(sum(1, 2)) // 3
console.log(sumArrow(1, 2)) // 3
```

### Arrow Function Syntax

```javascript
const functionName = (parameters) => {
  // function body
}
```

**Key differences from normal functions:**

1. Use `const` (or `let`) instead of `function` keyword
2. Function name comes first, then `=`
3. Parameters in parentheses
4. Arrow (`=>`) between parameters and body
5. Function body in curly braces

## Unique Features

For the most part you can use arrow functions just like normal functions, but they have some unique features you need to be aware of.

### Single Parameter Shortcut

When you have exactly **one parameter**, you can omit the parentheses:

<!-- prettier-ignore -->
```javascript
// With parentheses
const printName = (name) => {
  console.log(name)
}

// Without parentheses
const printNameShort = name => {
  console.log(name)
}
```

**Note:** If you have zero parameters or multiple parameters, parentheses are required:

```javascript
// Zero parameters - parentheses required
const sayHi = () => {
  console.log("Hi")
}

// Multiple parameters - parentheses required
const add = (x, y) => {
  return x + y
}
```

### Single Line Return Shortcut

When your function body is just **one line that returns a value**, you can use an even shorter syntax:

```javascript
// Normal arrow function
const sum = (a, b) => {
  return a + b
}

// Short arrow function (implicit return)
const sumShort = (a, b) => a + b

console.log(sumShort(1, 2)) // 3
```

JavaScript automatically returns the value after the arrow without needing `return` or curly braces it it just one line.

## Common Mistakes

1. Incorrect implicit return

   ```javascript
   // ❌ Wrong - can't use 'return' without curly braces
   const add = (a, b) => return a + b

   // ❌ Wrong - Doesn't return anything
   const add = (a, b) => {
     a + b
   }

   // ✅ Correct - either use curly braces with return
   const add = (a, b) => {
     return a + b
   }

   // ✅ Or use implicit return without curly braces
   const add = (a, b) => a + b
   ```

2. Forgetting Parentheses for Multiple Parameters

   ```javascript
   // ❌ Wrong - multiple parameters need parentheses
   const multiply = a, b => a * b

   // ✅ Correct
   const multiply = (a, b) => a * b
   ```

## When to Use Arrow Functions

```javascript
function processData(x, callback) {
  callback(x)
}

// With normal function (verbose)
processData(10, function (variable) {
  console.log(variable)
})

// With arrow function (concise)
processData(10, (variable) => {
  console.log(variable)
})

// Or even shorter on one line
processData(10, (variable) => console.log(variable))
```

**Use arrow functions for:**

- Short, simple functions
- Callback functions
- Anonymous functions
- Functions that fit on one line

**Consider normal functions for:**

- Functions that need a descriptive name

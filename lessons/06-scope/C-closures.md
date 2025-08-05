---
description: Learn how inner functions can access variables from outer scopes, even after the outer function has finished executing.
---

# Closures

Closures are one of JavaScript's most powerful features, but they often intimidate developers. If you've ever heard the word "closure" and immediately feared it because everyone said it's really difficult, don't worry! We've essentially already learned everything about closures when we studied scoping.

⚠️ **WARNING:** This is a tricky topic, so take your time to understand it fully!

## What is a Closure?

A closure happens when an inner function has access to variables from an outer scope. We've actually been using closures without realizing it!

### Simple Closure Example

```javascript
const a = 1

function print() {
  console.log(a) // Accessing variable from outer scope
}

print() // Prints: 1
```

This is technically a closure! The `print` function has access to the variable `a` from the outer scope.

### Closures with Dynamic Values

What makes closures confusing is they access the **current value** of variables, not the value they had when the closure was created:

```javascript
let a = 1

function print() {
  console.log(a)
}

a = 2 // Change the value before calling the function
print() // Prints: 2 (not 1!)
```

The function reads whatever the most recent value of `a` is when we actually call the function.

## Functions Inside Functions

The textbook example of closures involves functions inside other functions:

```javascript
function outer(a) {
  // This function returns another function
  function inner(b) {
    console.log(a) // From outer scope (outer function)
    console.log(b) // From current scope (inner function)
  }

  return inner // Return the inner function
}

// Create a new function by calling outer
const newFunc = outer(1)

// Call the returned function
newFunc(2)
// Output:
// 1
// 2
```

### How This Works Step by Step

1. We call `outer(1)`, which creates a function that "remembers" `a = 1`
2. `outer` returns the `inner` function
3. We store this returned function in variable `newFunc`
4. When we call `newFunc(2)`, it runs `inner(2)`, which:
   - Logs `a` (which is `1` from the outer scope)
   - Logs `b` (which is `2` from the current call)

## Accessing Multiple Scope Levels

Closures can access variables from multiple outer scopes:

```javascript
const c = 3 // Global scope

function outer(a) {
  function inner(b) {
    console.log(a) // From outer function scope
    console.log(b) // From inner function scope
    console.log(c) // From global scope
  }

  return inner
}

const newFunc = outer(1)
newFunc(2)
// Output:
// 1
// 2
// 3
```

The inner function has access to:

- Its own parameters (`b`)
- The outer function's parameters (`a`)
- Global variables (`c`)

## The Key Rule: One-Way Access

Remember the fundamental rule from scoping:

- ✅ **Inner scopes can read outer scopes**
- ❌ **Outer scopes cannot read inner scopes**

This is why closures work - the inner function can always access variables from outside.

## Why Closures Matter

Closures are extremely useful for:

1. **Function Factories** - Creating customized functions
2. **Callbacks** - Maintaining access to variables in asynchronous code

### Interview Questions

Closures are a favorite topic in JavaScript interviews. You might see code like this:

```javascript
function outer(x) {
  function inner(y) {
    console.log(x + y)
  }
  return inner
}

const addFive = outer(5)
addFive(3) // What does this print?
```

**Answer:** It prints `8` because:

- `outer(5)` creates a closure where `x = 5`
- Returns the `inner` function that remembers `x = 5`
- `addFive(3)` calls `inner(3)`, which logs `5 + 3 = 8`

## Practice Exercise

Create a function called `createGreeter` that:

1. Takes a `greeting` parameter (like "Hello" or "Hi")
2. Returns a function that takes a `name` parameter
3. The returned function should log the greeting + name

<details>
<summary>Solution</summary>

```javascript
function createGreeter(greeting) {
  return (name) => {
    console.log(greeting + " " + name)
  }
}

const sayHello = createGreeter("Hello")
const sayHi = createGreeter("Hi")

sayHello("Kyle") // "Hello Kyle"
sayHi("Sarah") // "Hi Sarah"
```

</details>

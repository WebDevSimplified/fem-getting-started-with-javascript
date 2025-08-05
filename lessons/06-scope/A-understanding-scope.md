---
description: Learn how JavaScript organizes variables and functions into different scopes, and how inner scopes can access outer scopes but not vice versa.
---

# Understanding Scope

Scope is a fundamental concept in JavaScript that determines where variables and functions can be accessed.

```javascript
function sayHi() {
  const result = "Hi"
  console.log(result) // Prints "Hi"
}

const result = "Bye"
sayHi() // What does this print?
console.log(result) // What does this print?
```

## What is Scope?

**Scope** is the area of your code where a variable or function is accessible. JavaScript creates a new scope inside every set of curly braces `{}` as well as a **global scope** for your entire file.

```javascript
function myFunction() {
  // New scope created here
  const x = 5
}

// Global scope
const x = 10
myFunction()
```

### Scope Is One-Way

The best way to think about scope is like **one-way mirrors** that always look outward:

- ✅ Inner scopes can see outer scopes

  ```javascript
  const a = 1 // Global scope

  function func() {
    const b = 2 // Function scope
    console.log(a) // ✅ Can see outer scope
    console.log(b) // ✅ Can see own scope
  }
  ```

- ❌ Outer scopes cannot see inner scopes

  ```javascript
  function func() {
    const b = 2 // Function scope
  }

  func()
  console.log(b) // ❌ Error - cannot see inner scope
  ```

## Types of Scope

There are multiple types of scope in JavaScript, but the three most important are **global scope**, **function scope**, and **block scope**.

### Global Scope

The **global scope** is the outermost scope - your entire file. Variables declared here can be accessed from anywhere in your code:

```javascript
const name = "Kyle" // Global scope

function sayHi() {
  console.log(name) // ✅ Can access global variable
}

sayHi()
```

### Block Scope

A new **block scope** is created for any code between curly braces `{}`:

```javascript
function myFunction() {
  const x = 3 // New block scope
}

if (true) {
  const x = 1 // New block scope
}

{
  const x = 2 // New block scope
}
```

### Function Scope

A **function scope** is created whenever you define a function. A function scope is very similar to a block scope, but some JavaScript features (covered later) use function scope instead of block scope:

```javascript
function myFunction() {
  const x = 5
}
```

## Nested Scopes

You can have multiple levels of scope:

```javascript
let c = 3 // Global scope

{
  // Outer block scope
  let a = 1

  {
    // Inner block scope
    let b = 2

    console.log(a) // 1 - can see outer scope
    console.log(b) // 2 - can see own scope
    console.log(c) // 3 - can see global scope
  }

  console.log(a) // 1 - can see own scope
  console.log(c) // 3 - can see global scope
  // console.log(b)  // ❌ Error - cannot see inner scope
}
```

### Naming Conflicts

You can have variables with the same name in different scopes without conflict:

```javascript
const result = "Kyle" // Global scope

function sayHi(name) {
  const result = "Hi " + name // Block scope - different variable!
  console.log(result) // "Hi Kyle"
}

sayHi("Kyle")
console.log(result) // "Kyle" - still the global variable
```

These are completely separate variables that happen to share a name.

### Determining Which Variable to Use

When JavaScript looks for a variable, it starts in the current scope and works outward:

```javascript
const a = 1 // Global scope
const name = "Kyle" // Global scope

function myFunction() {
  const a = 2 // Block scope

  console.log(a) // Prints 2
  console.log(name) // Prints "Kyle"
}

myFunction()
```

## Best Practices

- Minimize global variable usage

  ```javascript
  // ❌ Avoid this
  const name = "Kyle"

  function myFunction() {
    console.log(name)
  }
  ```

  ```javascript
  // ✅ Put variables as locally as possible
  function myFunction() {
    const name = "Kyle"
    console.log(name)
  }
  ```

- Don't use the same name for different variables in nested scopes

  ```javascript
  // ❌ Confusing - hard to tell which 'a' is used
  const a = 1

  function myFunction() {
    const a = 2
    console.log(a) // Which 'a' is this?
  }
  ```

  ```javascript
  // ✅ Clear - use different names
  const outerA = 1

  function myFunction() {
    const innerA = 2
    console.log(innerA) // Clearly uses inner scope
  }
  ```

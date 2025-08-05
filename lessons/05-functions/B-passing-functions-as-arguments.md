---
description: Learn how to pass functions to other functions as arguments, including callbacks and anonymous functions.
---

# Passing Functions as Arguments

One of the most powerful features of JavaScript is the ability to pass functions to other functions as arguments.

⚠️ **WARNING:** This is a tricky topic, so take your time to understand it fully!

## Functions are Variables

It's important to understand that **functions are just variables** that contain logic:

```javascript
function printName(name) {
  console.log(name)
}

// What happens if we log the function name without parentheses?
console.log(printName) // Prints: ƒ printName(name) { console.log(name) }
```

When you create a function with the `function` keyword, JavaScript creates a variable with that name and stores the function definition in it - just like how `let` creates a variable that stores a value.

## Basic Function Passing

Since functions are variables, you can pass them to other functions:

```javascript
function printName(name) {
  console.log(name)
}

function callFunction(x) {
  console.log("before")
  x("Kyle") // Call the function that was passed in
  console.log("after")
}

// Pass the function (note: no parentheses!)
callFunction(printName)
// Output:
// before
// Kyle
// after
```

### Key Point: Function vs Function Call

- `printVariable` - This is the function itself (the variable)
- `printVariable()` - This calls the function and runs the code inside it

## Callback Functions

When you pass a function to another function, that passed in function is called a **callback**:

```javascript
function sumCallback(a, b, callback) {
  let sum = a + b
  callback(sum) // Invoke the callback with the result
}

function handleSum(sum) {
  console.log(sum)
}

sumCallback(1, 2, handleSum) // Prints: 3
```

Here's what happens step by step:

1. `sumCallback` receives `1`, `2`, and the `handleSum` function
2. It calculates `1 + 2 = 3`
3. It calls the callback function (`handleSum`) with the result `3`
4. `handleSum` prints the `sum`

## Common Mistake: Calling Instead of Passing

A very common mistake is accidentally calling the function instead of passing it:

```javascript
function printName(name) {
  console.log(name)
}

function printGreeting(name, callback) {
  callback("Hello " + name)
}

// ❌ Wrong - this calls printName immediately
printGreeting("Kyle", printName())
// Result: undefined gets passed, then error "callback is not a function"

// ✅ Correct - this passes the function
printGreeting("Kyle", printName)
// Result: "Hello Kyle"
```

When you add parentheses, you're calling the function and passing its return value (which is `undefined` if the function doesn't return anything).

## Example Use Case

```javascript
function doMath(a, b, operation) {
  return operation(a, b)
}

function add(x, y) {
  return x + y
}

function subtract(x, y) {
  return x - y
}

console.log(doMath(5, 3, add)) // Prints: 8
console.log(doMath(5, 3, subtract)) // Prints: 2
```

## Practice Exercise

Try creating a function that:

1. Takes three parameters: a `firstName`, a `lastName`, and a `callback` function
2. Creates a `fullName` variable by combining the first and last names
3. Passes the `fullName` to the callback function (which prepends `"Hello "` to it)
4. Prints out the return of the callback function

<details>
<summary>Solution</summary>

```javascript
function printGreeting(firstName, lastName, callback) {
  const fullName = firstName + " " + lastName
  console.log(callback(fullName))
}

function getGreeting(name) {
  return "Hello " + name
}

printGreeting("Kyle", "Cook", getGreeting) // "Hello Kyle Cook"
```

</details>

## Why Use Callbacks?

1. **Flexibility** - The same function can behave differently based on the callback
2. **Separation of Concerns** - The main function handles one thing, the callback handles another

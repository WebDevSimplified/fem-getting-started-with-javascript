---
description: Learn how short-circuit evaluation works with logical operators to write more efficient and cleaner conditional code.
---

# Short-Circuit Evaluation

Short-circuit evaluation is a powerful feature of JavaScript's logical operators (`&&` and `||`) that can make your code more efficient and concise.

## What is Short-Circuit Evaluation?

Short-circuit evaluation means that JavaScript stops evaluating a logical expression as soon as it knows the final result. It "short-circuits" or skips the remaining parts of the expression.

## The `&&` (AND) Operator

With the AND operator, **both** operands must be `true` for the result to be `true`. If the first operand is `false`, JavaScript knows the entire expression will be `false`, so it doesn't evaluate the second operand.

```javascript
const a = false
const b = true

// JavaScript only checks 'a', sees it's false, and stops
const result = a && b
console.log(result) // false

// If we had an expensive function call:
function expensiveFunction() {
  console.log("This is an expensive operation!")
  return true
}

// expensiveFunction() is never called because a is false
const result2 = a && expensiveFunction()
console.log(result2) // false (and no console.log from expensiveFunction)
```

This makes `&&` perfect for conditional property access:

```javascript
// Safe property access
const user = null
user && user.name && console.log(user.name) // Won't error
```

## The `||` (OR) Operator

With the OR operator, if the first operand is `true`, JavaScript knows the entire expression will be `true`, so it doesn't evaluate the second operand.

```javascript
const a = true
const b = false

// JavaScript only checks 'a', sees it's true, and stops
const result = a || b
console.log(result) // true

function expensiveFunction() {
  console.log("This expensive function runs!")
  return false
}

// expensiveFunction() is never called because a is true
const result2 = a || expensiveFunction()
console.log(result2) // true (and no console.log from expensiveFunction)
```

This makes `||` perfect for providing fallback values:

```javascript
const userInput = ""
const defaultName = "Guest"

// If userInput is falsy, use defaultName
const displayName = userInput || defaultName
console.log(displayName) // "Guest"

// More examples
const config = {
  theme: null,
  timeout: 0,
}

const theme = config.theme || "light" // "light"
const timeout = config.timeout || 5000 // 5000
const debug = config.debug || false // false
```

## Return Values in Short-Circuit Evaluation

**Important:** Short-circuit operators don't just return `true` or `false` - they return the actual value that determined the result!

### AND `&&` Returns:

```javascript
// Returns the first falsy value, or the last value if all are truthy
console.log(false && "hello") // false
console.log(true && "hello") // "hello"
console.log("hi" && "bye") // "bye"
console.log("" && "hello") // "" (empty string is falsy)
console.log(5 && 10 && 15) // 15 (all truthy, returns last)
console.log(5 && 0 && 15) // 0 (first falsy value)
```

### OR `||` Returns:

```javascript
// Returns the first truthy value, or the last value if all are falsy
console.log(false || "hello") // "hello"
console.log(true || "hello") // true
console.log("hi" || "bye") // "hi"
console.log("" || "hello") // "hello"
console.log(null || undefined || "default") // "default"
console.log(0 || false || null) // null (all falsy, returns last)
```

## Modern Alternatives

JavaScript has introduced two new operators that can be used to replace some common short-circuit patterns:

### Nullish Coalescing `??`

The nullish coalescing operator only considers `null` and `undefined` as falsy so is perfect for default values when `0` or `false` are valid:

```javascript
const config = {
  timeout: 0, // We want to keep this 0!
  debug: null, // This should get a default
}

// Using || (considers 0 as falsy)
const timeout1 = config.timeout || 5000 // 5000 (❌)
const debug = config.debug ?? true // true (✅)

// Using ?? (only considers null/undefined as falsy)
const timeout2 = config.timeout ?? 5000 // 0 (✅)
const debug = config.debug ?? true // true (✅)
```

### Optional Chaining `?.`

Optional chaining will only access properties if the value before it is not `null` or `undefined`. This is great for safely accessing deeply nested properties:

```javascript
const user = {
  profile: {
    settings: {
      theme: "dark",
    },
  },
}

// Old way with &&
const theme1 =
  user && user.profile && user.profile.settings && user.profile.settings.theme

// New way with optional chaining
const theme2 = user?.profile?.settings?.theme

// Works with methods too
user?.notify?.()
```

---
description: Master advanced console methods and debugging techniques beyond basic console.log for more effective JavaScript debugging.
---

# Advanced Console Methods and Debugging

While `console.log()` is the most commonly used debugging method, the console object provides many more powerful methods that can significantly improve your debugging workflow. Let's explore these advanced console features and learn when and how to use them effectively.

## Console Methods by Category

### Different Log Levels

Different log levels help you categorize and filter your debugging output:

```javascript
// Information (same logging level as console.log)
console.info("Application started successfully")

// Warnings (yellow triangle icon)
console.warn("This feature will be deprecated in v2.0")

// Errors (red 'X' icon)
console.error("Failed to load user data")

// Debug (gray, often filtered out in production)
console.debug("Detailed debugging information")
```

**When to use each:**

- `console.info()`: General information about app state
- `console.warn()`: Potential problems that don't break functionality
- `console.error()`: Actual errors that need attention
- `console.debug()`: Detailed debugging info (often hidden by default)

#### Filtering Log Levels

You can filter console output by log level in the DevTools Console tab. This setting is generally in the top right and is a dropdown labeled "Default levels" or similar.

### Grouping Console Output

You can group related log messages together to keep your console organized:

```javascript
console.group("User Authentication")
console.log("Checking credentials...")
console.log("Username: Kyle")

console.group("Database Connection")
console.log("Connecting to database...")
console.log("Connection successful")
console.groupEnd() // Ends the Database Connection group

console.log("Authentication complete")
console.groupEnd() // Ends the User Authentication group
```

You can even start a group in a collapsed state:

```javascript
console.groupCollapsed("API Response Details")
console.log("Status: 200")
console.log("Headers: None")
console.log("Data: { name: 'Kyle' }")
console.groupEnd()
```

### Table Display

Display arrays in a clean table format:

```javascript
const users = [
  { id: 1, name: "Alice", age: 25, city: "New York" },
  { id: 2, name: "Bob", age: 30, city: "Los Angeles" },
  { id: 3, name: "Charlie", age: 35, city: "Chicago" },
]

// Display as a table
console.table(users)

// Display only specific columns
console.table(users, ["name", "age"])
```

### Assertions

By using `console.assert()`, you can test conditions and log messages only when the condition is false which can help clean up your logs when trying to debug specific issues:

```javascript
const age = 15
console.assert(age >= 18, "User must be 18 or older")

const response = { data: null }
console.assert(response.data !== null, "Response data should not be null")

// Won't log anything because condition is true
const validEmail = "user@example.com"
console.assert(validEmail.includes("@"), "Email must contain @")
```

I use `console.assert()` when I am trying to track why specific logic is not behaving as expected.

```javascript
const user = getUser()
console.assert(user != null, "One")

// Do something with user
console.assert(user != null, "Two")

// More logic
console.assert(user != null, "Three")

// Final logic
console.assert(user != null, "Four")
```

I can then look at my log output and see exactly where the user variable is becoming null.

### Timing Operations

Measure how long operations take:

```javascript
// Start timing
console.time("data-processing")

// Simulate some work
for (let i = 0; i < 1000000; i++) {
  // Some processing
}

// End timing and display result
console.timeEnd("data-processing") // Outputs: "data-processing: 5.2ms"
```

### Counting

Count how many times something happens:

```javascript
function processItem() {
  console.count("items processed")
  // Process the item
}

// Each call increments the counter
processItem() // items processed: 1
processItem() // items processed: 2
processItem() // items processed: 3

// Reset the counter
console.countReset("items processed")
processItem() // items processed: 1
```

### Stack Traces

See the call stack leading to a point in your code:

```javascript
function functionA() {
  functionB()
}

function functionB() {
  functionC()
}

function functionC() {
  console.trace("How did we get here?")
}

functionA()
// Shows the complete call stack: functionA → functionB → functionC
```

## Biggest `console.log()` Pitfall

By far the biggest problem developers run into with `console.log()` is not understanding why their objects/arrays are logging different information than they expect.

Take this example:

```javascript
const user = { name: "Alice", age: 25 }
console.log(user)
user.age = 26
```

If you look at the console output it may seem fine at first glance, but when you expand the logged object, you will see that it shows the updated age of 26 even though it was logged before the change. This is because `console.log()` gets the latest value of the object the first time you expand it.

### Fixing This Problem

The best way to fix this problem is to create a copy of the object/array when logging it:

```javascript
const user = { name: "Alice", age: 25 }
console.log(structuredClone(user))
user.age = 26
```

`structuredClone()` creates a deep copy of the object, so it is no longer tied to the original object. Now when you expand the logged object, it will show the original age of 25.

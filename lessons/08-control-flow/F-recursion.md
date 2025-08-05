---
description: Learn how recursion works - when functions call themselves to solve problems that can be broken down into smaller, similar subproblems.
---

# Recursion

Recursion is when a function calls itself. While this might sound strange at first, it's a powerful technique for solving problems that can be broken down into smaller, similar sub-problems.

⚠️ **WARNING:** This is a tricky topic, so take your time to understand it fully!

## Basic Recursion Example

Let's start with a simple recursive function that prints numbers:

```javascript
function printNumbers(number) {
  if (number > 10) {
    return // Base case: stop the recursion
  }

  console.log(number)
  printNumbers(number + 1) // Recursive call: function calls itself
}

printNumbers(1) // Prints: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
```

This replaces what you might do with a for loop:

```javascript
// For loop equivalent
for (let i = 1; i <= 10; i++) {
  console.log(i)
}
```

## Two Essential Parts of Recursion

Every recursive function needs these two components:

### 1. Base Case (Stopping Condition)

The condition that stops the recursion from continuing forever:

```javascript
if (number > 10) {
  return // This stops the recursion
}
```

Without a proper base case, you get infinite recursion and a **stack overflow error**:

```javascript
// ❌ This will crash!
function printHi() {
  console.log("Hi")
  printHi() // RangeError: Maximum call stack size exceeded
}

printHi()
```

### 2. Recursive Case (Self-Call)

The function calling itself with modified parameters:

```javascript
printNumbers(number + 1) // Calls itself with the next number
```

## Understanding the Call Stack

When a function calls itself, each call gets added to the call stack:

```javascript
function countdown(n) {
  console.log(n)
  if (n <= 0) return

  countdown(n - 1)
}

countdown(3)
```

**Call stack visualization:**

```text
countdown(3) calls countdown(2)
  countdown(2) calls countdown(1)
    countdown(1) calls countdown(0)
      countdown(0) returns
    countdown(1) returns
  countdown(2) returns
countdown(3) returns
```

## Recursion vs Loops

Let's compare solving the same problem with recursion and loops:

### Problem: Calculate factorial (5! = 5 × 4 × 3 × 2 × 1)

**With a for loop:**

```javascript
function factorialLoop(n) {
  let result = 1
  for (let i = 1; i <= n; i++) {
    result *= i
  }
  return result
}

console.log(factorialLoop(5)) // 120
```

**With recursion:**

```javascript
function factorialRecursive(n) {
  // Base case
  if (n <= 1) return 1

  // Recursive case
  return n * factorialRecursive(n - 1)
}

console.log(factorialRecursive(5)) // 120
```

**How `factorialRecursive(5)` works:**

```text
factorialRecursive(5) = 5 * factorialRecursive(4)
factorialRecursive(4) = 4 * factorialRecursive(3)
factorialRecursive(3) = 3 * factorialRecursive(2)
factorialRecursive(2) = 2 * factorialRecursive(1)
factorialRecursive(1) = 1 (base case)

Working backwards:
factorialRecursive(1) = 1
factorialRecursive(2) = 2 * 1 = 2
factorialRecursive(3) = 3 * 2 = 6
factorialRecursive(4) = 4 * 6 = 24
factorialRecursive(5) = 5 * 24 = 120
```

## When to Use Recursion

1. Tree-like Data Structures

   ```javascript
   const fileSystem = {
     name: "root",
     type: "folder",
     children: [
       {
         name: "documents",
         type: "folder",
         children: [
           { name: "resume.pdf", type: "file" },
           { name: "notes.txt", type: "file" },
         ],
       },
       {
         name: "photos",
         type: "folder",
         children: [{ name: "vacation.jpg", type: "file" }],
       },
       { name: "readme.txt", type: "file" },
     ],
   }

   // Count all files in the file system
   function countFiles(item) {
     // Base case: if it's a file, count it
     if (item.type === "file") return 1

     // Recursive case: if it's a folder, count files in all children
     let count = 0
     for (const child of item.children) {
       count += countFiles(child) // Recursive call for each child
     }
     return count
   }

   console.log(countFiles(fileSystem)) // 4 files total
   ```

2. Mathematical Sequences

   **Fibonacci sequence:** Each number is the sum of the two preceding numbers (0, 1, 1, 2, 3, 5, 8, 13...)

   ```javascript
   function fibonacci(n) {
     // Base cases
     if (n <= 0) return 0
     if (n === 1) return 1

     // Recursive case
     return fibonacci(n - 1) + fibonacci(n - 2)
   }

   console.log(fibonacci(6)) // 8
   console.log(fibonacci(10)) // 55
   ```

3. Processing Nested Objects

   ```javascript
   const person = {
     name: "Kyle",
     friend: {
       name: "Joe",
       friend: {
         name: "Sally",
         friend: null,
       },
     },
   }

   // Find the person at the end of the friend chain
   function findLastFriend(person) {
     // Base case: no more friends
     if (person.friend === null) return person.name

     // Recursive case: check the friend's friend
     return findLastFriend(person.friend)
   }

   console.log(findLastFriend(person)) // "Sally"
   ```

## Common Mistakes

1. Forgetting the Base Case

   ```javascript
   // ✅ Good - has base case
   function countdown(n) {
     if (n <= 0) return // Base case
     console.log(n)
     countdown(n - 1)
   }

   // ❌ Bad - no base case
   function badCountdown(n) {
     console.log(n)
     badCountdown(n - 1) // This will run forever!
   }
   ```

2. Not Moving Toward the Base Case

   ```javascript
   // ✅ Good - n gets smaller each time
   function countdown(n) {
     if (n <= 0) return
     console.log(n)
     countdown(n - 1) // Moving toward base case
   }

   // ❌ Bad - n never changes
   function badCountdown(n) {
     if (n <= 0) return
     console.log(n)
     countdown(n) // n never changes!
   }
   ```

## When to Use Recursion

**✅ Use recursion when:**

- Working with tree-like or nested data structures
- The problem can be broken into smaller, similar sub-problems
- The recursive solution is clearer than the iterative one
- Processing hierarchical data (file systems, organizational charts, etc.)

**❌ Avoid recursion when:**

- A simple loop would work just as well
- Performance is critical (recursion has overhead)
- The recursive solution is hard to understand

## Exercise

Write a recursive function that finds the maximum value in a nested array structure like this:

```javascript
const data = [1, [2, 3], [4, [5, 6]], 7]
// Should return 7
// You can use Array.isArray() to check if an item is an array
```

<details>
<summary>Solution</summary>

```javascript
function findMax(arr) {
  let max = -Infinity

  for (const item of arr) {
    if (Array.isArray(item)) {
      // Recursive case: if item is an array, find max in that array
      const subMax = findMax(item)
      max = Math.max(max, subMax)
    } else {
      // Base case: if item is a number, compare with current max
      max = Math.max(max, item)
    }
  }

  return max
}

const data = [1, [2, 3], [4, [5, 6]], 7]
console.log(findMax(data)) // 7
```

</details>

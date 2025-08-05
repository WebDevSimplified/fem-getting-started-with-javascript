---
description: Learn how to use for loops to repeat code a specific number of times and iterate over data structures.
---

# For Loops

For loops are used when you need to repeat code a specific number of times. They're perfect for counting, iterating through arrays, or any task that needs to be done repeatedly.

## Basic For Loop Syntax

A for loop has three main parts separated by semicolons and then a body enclosed in curly braces:

```javascript
for (let i = 0; i < 5; i++) {
  console.log(`Count: ${i}`)
}
// Output:
// Count: 0
// Count: 1
// Count: 2
// Count: 3
// Count: 4
```

1. `let i = 0` - This first part runs once at the start of your loop. It usually creates a variable to keep track of the loop count.
2. `i < 5` - The second part is the condition that is checked before each iteration. If it's true, the code in the loop runs; if false, the loop stops.
3. `i++` - The third part runs after each iteration. It usually updates the loop variable (in this case, adding 1 to `i`).
4. `{ ... }` - The curly braces contain the code that runs each time the loop iterates.

### Simple Counting Example

Let's print `"Hi"` five times:

```javascript
// Without a loop (repetitive)
console.log("Hi")
console.log("Hi")
console.log("Hi")
console.log("Hi")
console.log("Hi")

// With a for loop (clean)
for (let i = 0; i < 5; i++) {
  console.log("Hi")
}
```

Both produce the same output, but the for loop is much more maintainable.

## Common Loop Patterns

- Counting Up

  ```javascript
  // Count from 1 to 10
  for (let i = 1; i <= 10; i++) {
    console.log(i)
  }
  ```

- Counting Down

  ```javascript
  // Count down from 10 to 1
  for (let i = 10; i >= 1; i--) {
    console.log(i)
  }
  ```

- Skip Numbers

  ```javascript
  // Even numbers only
  for (let i = 0; i <= 10; i += 2) {
    console.log(i) // 0, 2, 4, 6, 8, 10
  }

  // Every third number
  for (let i = 0; i <= 20; i += 3) {
    console.log(i) // 0, 3, 6, 9, 12, 15, 18
  }
  ```

## Iterating Through Arrays

For loops are perfect for going through every item in an array:

```javascript
const fruits = ["apple", "banana", "orange", "grape"]

// Print with index
for (let i = 0; i < fruits.length; i++) {
  console.log(`${i}: ${fruits[i]}`)
}
// Output:
// 0: apple
// 1: banana
// 2: orange
// 3: grape
```

## Nested For Loops

You can put for loops inside other for loops:

```javascript
// Multiplication table
for (let i = 1; i <= 3; i++) {
  for (let j = 1; j <= 3; j++) {
    console.log(`${i} × ${j} = ${i * j}`)
  }
}
// Output:
// 1 × 1 = 1
// 1 × 2 = 2
// 1 × 3 = 3
// 2 × 1 = 2
// 2 × 2 = 4
// 2 × 3 = 6
// 3 × 1 = 3
// 3 × 2 = 6
// 3 × 3 = 9
```

## Loop Control Statements

- `break` - Exit the Loop Early

  ```javascript
  // Find the first number greater than 5
  const numbers = [1, 3, 7, 2, 9, 4]

  for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] > 5) {
      console.log(`Found: ${numbers[i]} at index ${i}`)
      break // Exit the loop immediately
    }
  }
  // Output: Found: 7 at index 2
  ```

- `continue` - Skip to Next Iteration

  ```javascript
  // Print all numbers except 3
  for (let i = 1; i <= 5; i++) {
    if (i === 3) {
      continue // Skip 3
    }
    console.log(i)
  }
  // Output: 1, 2, 4, 5
  ```

## For Loop Alternatives

- For...of Loop (for arrays)

  ```javascript
  const fruits = ["apple", "banana", "orange"]

  // Traditional for loop
  for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i])
  }

  // For...of loop
  for (const fruit of fruits) {
    console.log(fruit)
  }
  // Output:
  // apple
  // banana
  // orange
  ```

- For...in Loop (for object properties)

  ```javascript
  const person = {
    name: "Kyle",
    age: 25,
    city: "New York",
  }

  for (const key in person) {
    console.log(`${key}: ${person[key]}`)
  }
  // Output:
  // name: Kyle
  // age: 25
  // city: New York
  ```

## Common Mistakes

1. Infinite Loops

   Always ensure your loop condition will eventually become false.

   ```javascript
   // ❌ Infinite loop
   for (let i = 0; i < 10; i--) {
     console.log(i) // This will run forever!
   }
   ```

   **Signs of infinite loops:**

   - Your browser/program becomes unresponsive
   - Console keeps printing the same thing
   - You need to force-quit your program

2. Off-by-One Errors

   Make sure your loop conditions are correct to avoid missing the last item or going out of bounds.

   ```javascript
   const arr = [10, 20, 30]

   // ❌ Off-by-one error - misses last item
   for (let i = 0; i < arr.length - 1; i++) {
     console.log(arr[i]) // Only prints 10, 20
   }

   // ❌ Off-by-one error - goes out of bounds
   for (let i = 0; i <= arr.length; i++) {
     console.log(arr[i]) // Prints 10, 20, 30, undefined
   }

   // ✅ Correct
   for (let i = 0; i < arr.length; i++) {
     console.log(arr[i]) // Prints 10, 20, 30
   }
   ```

3. Modifying the Loop Variable Inside the Loop

   Avoid changing the loop variable inside the loop body, as it can lead to unexpected behavior.

   ```javascript
   // ❌ Modifying loop variable
   for (let i = 0; i < 5; i++) {
     console.log(i)
     if (i === 1) {
       i += 2 // This will skip numbers
     }
   }
   // Output: 0, 1, 4

   // ✅ Don't modify the loop variable
   for (let i = 0; i < 5; i++) {
     console.log(i)
   }
   // Output: 0, 1, 2, 3, 4
   ```

## Exercise

Write a for loop that:

1. Creates an array of the first 10 even numbers (2, 4, 6, 8, ...)
2. Then calculates the sum of those numbers in a second loop
3. Finally, prints the array and the sum

<details>
<summary>Solution</summary>

```javascript
// Create array of first 10 even numbers
const evenNumbers = []
for (let i = 1; i <= 10; i++) {
  evenNumbers.push(i * 2)
}

// Calculate sum
let sum = 0
for (let i = 0; i < evenNumbers.length; i++) {
  sum += evenNumbers[i]
}

console.log("Even numbers:", evenNumbers) // [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
console.log("Sum:", sum) // 110
```

</details>

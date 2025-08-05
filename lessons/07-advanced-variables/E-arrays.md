---
description: Learn how to create and work with arrays to store multiple values in a single variable.
---

# Arrays

Up until now, we've been creating variables that store a single value, but what if we want to store multiple values in one variable? This is where **arrays** come in!

## What is an Array?

An array is a list of values stored in a single variable. Think of it like a container that can hold multiple items.

```javascript
// Single values
const number = 5
const name = "Kyle"

// Multiple values in an array
const numbers = [1, 2, 3, 4, 5]
const names = ["Kyle", "Sarah", "John"]
```

## Creating Arrays

To create an array, use square brackets `[]` and separate values with commas:

```javascript
const letters = ["A", "B", "C", "D", "E"]
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

You can format arrays on multiple lines for readability:

```javascript
const longList = [
  "Kyle",
  "Sarah",
  "John",
  "Alice",
  "Bob",
  "Charlie",
  "Mike",
  "Emma",
]
```

## Accessing Array Elements

Use square brackets with a number corresponding to the position of the element in the array to access it:

```javascript
const numbers = [1, 2, 3, 4, 5]

console.log(numbers[0]) // 1 (first element)
console.log(numbers[1]) // 2 (second element)
console.log(numbers[4]) // 5 (fifth element)
```

### IMPORTANT: Arrays Start at Index 0!

This is one of the most common sources of confusion:

```javascript
const letters = ["A", "B", "C"]

// To get the FIRST letter, use index 0
console.log(letters[0]) // "A"

// To get the SECOND letter, use index 1
console.log(letters[1]) // "B"

// To get the THIRD letter, use index 2
console.log(letters[2]) // "C"
```

## Adding Elements to Arrays

Use the `push()` method to add elements to the end of an array:

```javascript
const numbers = [1, 2, 3]
console.log(numbers) // [1, 2, 3]

numbers.push(4)
console.log(numbers) // [1, 2, 3, 4]

numbers.push(5)
console.log(numbers) // [1, 2, 3, 4, 5]
```

## Mixed Data Types

JavaScript arrays can contain different types of data:

```javascript
const mixedArray = [1, "hello", true, 3.14, null]

console.log(mixedArray[0]) // 1 (number)
console.log(mixedArray[1]) // "hello" (string)
console.log(mixedArray[2]) // true (boolean)
```

While this is possible, it's generally better to keep arrays consistent (all numbers, all strings, etc.).

## Nested Arrays

You can put arrays inside other arrays:

```javascript
const nestedArray = [
  ["A", "B"],
  ["C", "D"],
]

console.log(nestedArray[0]) // ["A", "B"]
console.log(nestedArray[1]) // ["C", "D"]
```

### Accessing Nested Elements

Use multiple sets of brackets to access nested elements:

```javascript
const grid = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
]

// Get the first row
console.log(grid[0]) // [1, 2, 3]

// Get the middle element (5)
console.log(grid[1][1]) // 5

// Get the bottom-right element (9)
console.log(grid[2][2]) // 9
```

## Array Length

Every array has a `length` property that tells you how many elements it contains:

```javascript
const colors = ["red", "green", "blue"]
console.log(colors.length) // 3

const empty = []
console.log(empty.length) // 0
```

## Practice Exercise

Create an array with the first 5 letters of the alphabet, then print out the middle element (which should be "C").

<details>
<summary>Solution</summary>

```javascript
const letters = ["A", "B", "C", "D", "E"]

// The middle element is at index 2 (remember: start counting at 0)
console.log(letters[2]) // "C"
```

</details>

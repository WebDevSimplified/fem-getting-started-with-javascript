---
description: Learn essential array methods like forEach, map, filter, find, some, every, and reduce to work with arrays efficiently in JavaScript.
---

# Array Methods

Arrays are incredibly powerful in JavaScript, and they become even more useful when you know the built-in methods that can help you work with them efficiently.

## What Are Array Methods?

Array methods are functions that are built into JavaScript arrays. You call them using dot notation on an array, just like accessing properties on objects.

```javascript
const numbers = [1, 2, 3, 4, 5]

numbers.forEach((n) => {
  // Do something with each number
})
```

## `forEach` Method

`forEach` is probably the most commonly used array method. It loops through each element in your array and runs a function for each one.

```javascript
const numbers = [1, 2, 3, 4, 5]

numbers.forEach((number) => {
  console.log(number)
})

// Prints:
// 1
// 2
// 3
// 4
// 5
```

### `forEach` with Index

`forEach` can also give you the index of each element:

```javascript
const names = ["Kyle", "Sarah", "John"]

names.forEach((name, index) => {
  console.log(`${name} ${index}`)
})

// Prints:
// Kyle 0
// Sarah 1
// John 2
```

The index corresponds to the bracket notation you'd use to access that element:

```javascript
console.log(numbers[0]) // 1 (same as first forEach iteration)
console.log(numbers[1]) // 2 (same as second forEach iteration)
```

## `map` Method

`map` is similar to `forEach`, but with a key difference: it **returns a new array** based on what you return from your function.

```javascript
const numbers = [1, 2, 3, 4, 5]

const doubled = numbers.map((number) => {
  return number * 2
})

console.log(doubled) // [2, 4, 6, 8, 10]
console.log(numbers) // [1, 2, 3, 4, 5] (original unchanged)
```

### Key Points About `map`:

- **Returns a new array** - doesn't modify the original
- **Same length** - new array has same number of elements
- **Transform each element** - each element can become something new

### Common Use Case

```javascript
const people = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" },
  { id: 3, name: "Charlie" },
]

const names = people.map((person) => {
  return person.name
})
console.log(names) // ["Alice", "Bob", "Charlie"]
```

## `filter` Method

`filter` creates a new array containing only the elements that pass a test. You return `true` to keep an element, `false` to remove it.

```javascript
const numbers = [1, 2, 3, 4, 5]

const smallNumbers = numbers.filter((number) => {
  return number <= 2
})

console.log(smallNumbers) // [1, 2]
console.log(numbers) // [1, 2, 3, 4, 5] (original unchanged)
```

## `find` Method

`find` is similar to `filter`, but it only returns the **first** element that matches your condition. As soon as it finds a match, it stops looking.

```javascript
const numbers = [1, 2, 3, 4, 5]

const firstBigNumber = numbers.find((number) => {
  return number > 2
})

console.log(firstBigNumber) // 3 (not an array, just the number)
```

## `some` Method

`some` checks if **at least one** element in your array passes a test. It returns `true` or `false`.

```javascript
const numbers = [1, 2, 3, 4, 5]

const hasLargeNumber = numbers.some((number) => {
  return number > 3
})
console.log(hasLargeNumber) // true (because 4 and 5 are > 3)

const hasNegativeNumber = numbers.some((number) => {
  return number < 0
})
console.log(hasNegativeNumber) // false (no numbers are < 0)
```

### How `some` Works:

- **Returns true** if ANY element passes the test
- **Returns false** if NO elements pass the test
- **Stops checking** as soon as it finds one that passes

## `every` Method

`every` is the opposite of `some` - it checks if **ALL** elements pass a test.

```javascript
const numbers = [1, 2, 3, 4, 5]

const allPositive = numbers.every((number) => {
  return number > 0
})
console.log(allPositive) // true (all numbers are greater than 0)

const allLarge = numbers.every((number) => {
  return number > 3
})
console.log(allLarge) // false (1, 2, and 3 are not > 3)
```

### How `every` Works:

- **Returns true** if ALL elements pass the test
- **Returns false** if ANY element fails the test
- **Stops checking** as soon as it finds one that fails

## `reduce` Method

`reduce` is the most powerful (and confusing) array method. It "reduces" your array down to a single value by running a function that gathers the results into a single value.

```javascript
const numbers = [1, 2, 3, 4, 5]

const sum = numbers.reduce((accumulator, number) => {
  return accumulator + number
}, 0) // 0 is the starting value

console.log(sum) // 15 (0+1+2+3+4+5)
```

### How `reduce` Works:

1. **Starting value**: The second argument (0 in the example above)
2. **Accumulator**: Starts as the starting value, then becomes whatever you return
3. **Current element**: Each element in the array, one by one
4. **Return value**: Becomes the new accumulator for the next iteration

Let's trace through the sum example:

```javascript
const numbers = [1, 2, 3, 4, 5]

const sum = numbers.reduce((accumulator, number) => {
  console.log(`accumulator: ${accumulator}, number: ${number}`)
  return accumulator + number
}, 0)

// Prints:
// accumulator: 0, number: 1 → returns 1
// accumulator: 1, number: 2 → returns 3
// accumulator: 3, number: 3 → returns 6
// accumulator: 6, number: 4 → returns 10
// accumulator: 10, number: 5 → returns 15

console.log(sum) // 15
```

---
description: Learn the crucial difference between how JavaScript handles primitive values versus object references.
---

# Reference vs Value

One of the most important concepts to understand in JavaScript is how variables store data in your computer's memory. There are two main categories of data types: **value types** (primitives) and **reference types** (objects, arrays, functions).

⚠️ **WARNING:** This is a tricky topic, so take your time to understand it fully!

## How Value Types Work

When you assign primitive values, JavaScript copies the actual value directly into your computer's memory:

```javascript
const a = 10
const b = "hi"
```

<div style="max-width: 500px;">

| Variable | Value  |
| -------- | ------ |
| `a`      | `10`   |
| `b`      | `"hi"` |

</div>

### Copying Value Types

When you copy a variable that holds a primitive value, JavaScript creates a completely new copy of that value in memory:

```javascript
let a = 10
let b = a // Copies the VALUE of a

b = b + 1 // Only changes b, not a
```

<div style="max-width: 500px;">

| Variable | Value |
| -------- | ----- |
| `a`      | `10`  |
| `b`      | `11`  |

</div>

## How Reference Types Work

When you create arrays or objects, JavaScript stores a **reference** (memory address) to where the data lives:

```javascript
const c = [1, 2]
```

<div class="side-by-side-tables">

| Variable | Value (Reference) |
| -------- | ----------------- |
| `c`      | `0x001`           |

| Memory Location | Actual Data |
| --------------- | ----------- |
| `0x001`         | `[1, 2]`    |

</div>

Think of `0x001` as a "hotel room number" - the variable stores the room number, not the actual contents of the room.

### Copying Reference Types

When you copy a variable that holds an array or object, JavaScript copies the **reference** (memory address), not the actual data:

```javascript
const c = [1, 2]
const d = c // Copies the REFERENCE, not the array

d.push(3) // Modifies the array that both c and d point to
```

<div class="side-by-side-tables">

| Variable | Value (Reference) |
| -------- | ----------------- |
| `c`      | `0x001`           |
| `d`      | `0x001`           |

| Memory Location | Actual Data |
| --------------- | ----------- |
| `0x001`         | `[1, 2, 3]` |

</div>

Both `c` and `d` store the same memory address (`0x001`), so they both point to the same array in memory.

## Creating New References

When you create a new array/object, JavaScript allocates a new memory location:

```javascript
let c = [1, 2] // Memory location 0x001
let d = [3, 4, 5] // Memory location 0x002 (different!)

d.push(6)
```

<div class="side-by-side-tables">

| Variable | Value (Reference) |
| -------- | ----------------- |
| `c`      | `0x001`           |
| `d`      | `0x002`           |

| Memory Location | Actual Data    |
| --------------- | -------------- |
| `0x001`         | `[1, 2]`       |
| `0x002`         | `[3, 4, 5, 6]` |

</div>

### Comparing References

Since JavaScript compares the `Value (Reference)` column and not the actual contents, two different arrays/objects with the same contents are considered different:

```javascript
const a = [1, 2]
const b = [1, 2] // Same contents, but different memory locations!

console.log(a == b) // false
console.log(a === b) // false
```

<div class="side-by-side-tables">

| Variable | Value (Reference) |
| -------- | ----------------- |
| `a`      | `0x001`           |
| `b`      | `0x002`           |

| Memory Location | Actual Data |
| --------------- | ----------- |
| `0x001`         | `[1, 2]`    |
| `0x002`         | `[1, 2]`    |

</div>

JavaScript is asking: "Is `0x001` the same as `0x002`?" The answer is no, even though the contents are identical.

#### When Equality Returns True

```javascript
const a = [1, 2]
const b = a // Same reference!

console.log(a === b) // true ← Both point to same memory location
```

#### Objects Work the Same Way

```javascript
let person1 = { name: "Kyle" }
let person2 = person1 // Same reference

person2.name = "Joe"

console.log(person1.name) // "Joe" ← Changed!
console.log(person2.name) // "Joe" ← Same object
console.log(person1 === person2) // true ← Same reference

// But creating a new object:
const person3 = { name: "Joe" }
console.log(person1 === person3) // false ← Different references
```

### `const` with References

The `const` keyword prevents you from reassigning a variable, but it doesn't prevent you from modifying the contents of arrays/objects declared with `const`.

`const` only cares about the `Value (Reference)` column.

```javascript
const arr = [1, 2]

// This works! We're not changing the reference
arr.push(3)
console.log(arr) // [1, 2, 3]

// This fails! We're trying to change the reference
arr = [4, 5, 6] // ❌ TypeError: Assignment to constant variable
```

<div style="max-width: 500px;">

| Variable | Value (Reference) |
| -------- | ----------------- |
| `a`      | `0x001`           |

</div>

## Functions and References

When you pass arrays/objects to functions, you're passing the reference which means the function can modify the original data:

```javascript
function addElement(array, element) {
  array.push(element) // Modifies the original array!
}

const numbers = [1, 2, 3]
addElement(numbers, 4)

console.log(numbers) // [1, 2, 3, 4] ← Original array modified
```

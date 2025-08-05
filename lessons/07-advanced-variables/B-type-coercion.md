---
description: Learn how JavaScript automatically converts between types and how to prevent unexpected behavior with proper equality operators.
---

# Type Coercion

Type coercion is JavaScript's way of automatically converting one data type to another. While this can be convenient, it often leads to confusing and unexpected behavior.

## JavaScript Data Types Recap

Before diving into type coercion, let's review the main data types in JavaScript:

- **Numbers** - `1`, `2.5`, `-10`
- **Strings** - `"hello"`, `"123"`
- **Booleans** - `true`, `false`
- `null` - Represents intentional absence of value
- `undefined` - Represents uninitialized or missing value

## Explicit Type Coercion

Explicit type coercion is when **you** tell JavaScript to convert one type to another.

### Converting Strings to Numbers

```javascript
const a = "1"
console.log(typeof a) // "string"

// Convert to integer
const numberA = parseInt(a)
console.log(typeof numberA) // "number"
```

#### parseInt vs parseFloat

- **parseInt** - Converts to whole numbers (integers)
- **parseFloat** - Converts to decimal numbers (floats)

```javascript
let decimal = "1.3"

console.log(parseInt(decimal)) // 1 (removes decimal part)
console.log(parseFloat(decimal)) // 1.3 (keeps decimal)
```

### Converting Variables to Strings

```javascript
const num = 1.34
const stringNum = num.toString()

console.log(typeof stringNum) // "string"
```

## Implicit Type Coercion

Implicit type coercion happens when JavaScript **automatically** converts types for you without you asking for it. This is where things can get confusing.

### The Plus `+` Operator Problem

When you use `+` with strings and numbers, JavaScript converts the number to a string:

```javascript
const a = 1 // number
const b = "3" // string

console.log(a + b) // "13" (not 4)
```

This is the same as writing:

```javascript
console.log(a.toString() + b) // "13"
```

To fix this do explicit type coercion:

```javascript
console.log(a + parseInt(b)) // 4 (proper addition)
```

### Other Operators Behave Differently

Unlike `+`, other mathematical operators convert strings to numbers:

```javascript
const a = 3 // number
const b = "1" // string

console.log(a - b) // 2 (converts "1" to 1, then 3 - 1)
console.log(a * b) // 3 (converts "1" to 1, then 3 * 1)
```

## Which To Use?

Generally it is best to avoid implicit coercion because it can lead to unexpected results. Instead, use explicit conversion functions like `parseInt`, `parseFloat`, or `toString` when you need to convert types.

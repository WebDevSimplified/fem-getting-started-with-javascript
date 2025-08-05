---
title: NaN (Not a Number)
description: Learn about NaN (Not a Number) and how to properly check for it in JavaScript.
---

# `NaN` (Not a Number)

`NaN` is a special value in JavaScript that stands for "Not a Number".

## What Causes `NaN`?

`NaN` occurs when you attempt to convert non-numeric variables (such as strings) to numbers:

```javascript
const result = parseInt("hello")

console.log(result) // NaN
console.log(typeof result) // "number"
```

Even though `NaN` means "Not a Number", its type is actually `"number"`.

## Checking for `NaN`

You might think you can check for `NaN` like this, but it doesn't work:

```javascript
const a = parseInt("hello")

console.log(a == NaN) // false
```

**Why doesn't this work?** `NaN` is never equal to anything, including itself!

```javascript
console.log(NaN == NaN) // false
```

### The Correct Way: `isNaN()`

To check if a value is `NaN`, use the built-in `isNaN()` function:

```javascript
const a = parseInt("hello") // NaN
const b = 5 // number

console.log(isNaN(a)) // true (a is NaN)
console.log(isNaN(b)) // false (b is a valid number)
```

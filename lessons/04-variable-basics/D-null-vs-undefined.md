---
description: Learn about JavaScript's special values null and undefined, understand their differences, and know when to use each one.
---

# Representing "Nothing"

Representing the lack of a value is confusing in JavaScript since there are two different ways to do it: `null` and `undefined`.

## What Are `null` and `undefined`?

Both `null` and `undefined` represent the lack of a value, but they're used in different situations:

- `undefined` - means a variable exists but hasn't been given a value yet
- `null` - means you've intentionally set a variable to have no value

## Understanding `undefined`

When you create a variable but don't give it a value, JavaScript automatically sets it to `undefined`:

```javascript
let a
console.log(a) // undefined
```

There are other cases where you might see `undefined`, which will be covered later, but it always means a value does not exist.

## Understanding `null`

`null` is a value used to indicate "intentionally empty":

```javascript
let a = null
console.log(a) // null
```

By setting a value to `null`, you are explicitly saying this variable has **no value**.

## Best Practices

1. Use `null` for Intentional "Empty" States

   ```javascript
   let selectedFile = null
   let currentTheme = null
   let lastError = null
   ```

2. Let `undefined` Happen Naturally

   ```javascript
   let userName // Will be set later
   let userPreferences // Will be loaded from server
   ```

3. Use `null` to Clear Values

   ```javascript
   let name = "Kyle"
   // Other code uses name...
   name = null // Now name has no value
   ```

## The Key Difference

- `undefined` - I haven't been given a value yet
- `null` - I specifically have no value

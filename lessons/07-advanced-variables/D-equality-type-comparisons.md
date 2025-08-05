---
description: Learn how JavaScript handles equality comparisons and the importance of using strict equality.
---

# Equality: `==` vs `===`

JavaScript has two ways to check equality, and they behave very differently.

## Double Equals `==` - With Type Coercion

The `==` operator performs type coercion before comparing:

```javascript
console.log(1 == "1") // true (converts string "1" to number 1)

console.log(0 == false) // true (0 is "falsy")
console.log("" == false) // true (empty string is "falsy")
```

**Why?** JavaScript converts these values to the same type before comparing. Zero and empty strings are considered "falsy" values that equal `false`.

## Triple Equals `===` - No Type Coercion

The `===` operator compares both value **and** type without any coercion:

```javascript
console.log(1 === 1) // true (same type and value)
console.log(1 === "1") // false (different types)
console.log(0 === false) // false (different types)
console.log("" === false) // false (different types)
```

## Not Equals: `!=` vs `!==`

The same rules apply to not equals:

```javascript
console.log(1 != "1") // false (converts types, then compares)
console.log(1 !== "1") // true (different types, so not equal)
```

## Which To Use?

**Always prefer `===` and `!==`** to avoid unexpected type coercion issues.

### The Exception: `null` and `undefined`

There's one case where `==` is actually useful - checking for `null` or `undefined`:

```javascript
console.log(null == null) // true
console.log(null == undefined) // true (null and undefined are considered equal)

console.log(null === null) // true
console.log(null === undefined) // false (different types)
```

When checking if a variable has a value, you often want to catch both `null` and `undefined` which is why `==` is useful here.

---
description: Learn how to write concise conditional logic using the ternary operator for simple if-else scenarios.
---

# Ternary Operator

The ternary operator is a shorthand way to write simple if-else statements. It's called "ternary" because it takes three operands (parts).

## Basic Syntax

```javascript
const age = 18

age >= 18 ? "trueValue" : "falseValue"
```

Think of `?` as "if" and `:` as "else". If the condition before `?` is true, it returns the value after the `?`; otherwise, it returns the value after the `:`.

### Ternaries Return Values

Another useful feature of the ternary operator is that it **always returns a value**. This makes it great for assignments:

```javascript
// Traditional if-else
let message
if (age >= 18) {
  message = "You can vote"
} else {
  message = "You cannot vote"
}
```

```javascript
// Ternary operator
const message = age >= 18 ? "You can vote" : "You cannot vote"
```

## Chaining Ternary Operators

You can chain multiple ternaries together, but be careful as it can get hard to read:

```javascript
// This works but can be hard to read
const grade = score >= 90 ? "A" : score >= 80 ? "B" : score >= 70 ? "C" : "F"

// If-else is clearer
let grade
if (score >= 90) {
  grade = "A"
} else if (score >= 80) {
  grade = "B"
} else if (score >= 70) {
  grade = "C"
} else {
  grade = "F"
}
```

## When to Use Ternary Operators

✅ **Good for:**

- Simple conditions with two outcomes
- Assigning values based on conditions
- Short, readable expressions

❌ **Avoid for:**

- Complex conditions
- Multiple statements in each branch
- Nested ternary operators

## Exercise

Convert this if-else statement to a ternary operator:

```javascript
let weather
if (temperature > 75) {
  weather = "hot"
} else {
  weather = "not hot"
}
```

<details>
<summary>Solutions</summary>

```javascript
const weather = temperature > 75 ? "hot" : "not hot"
```

</details>

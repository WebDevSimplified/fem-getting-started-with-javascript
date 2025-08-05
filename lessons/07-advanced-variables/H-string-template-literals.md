---
description: Learn how to use template literals (backticks) to create dynamic strings with embedded variables and expressions.
---

# String Template Literals

So far we've been creating strings using single quotes `''` or double quotes `""`, but JavaScript provides a third way to create strings that's much more powerful: **template literals** using backticks ` `` `.

## Basic Template Literal Syntax

Instead of regular quotes, template literals use backticks (the key above `Tab` on most keyboards):

```javascript
const a = `Hi`
console.log(a) // Hi
```

This works exactly the same as regular strings, but template literals have a special superpower.

### Embedding Variables with `${}`

The real power of template literals comes from being able to embed variables directly inside your strings using `${}` syntax:

```javascript
const firstName = "Kyle"
const lastName = "Cook"

console.log(firstName + " " + lastName) // Kyle Cook
console.log(`${firstName} ${lastName}`) // Kyle Cook
```

The `${}` syntax tells JavaScript "run the code inside these brackets and put the result here."

### Embedding Any JavaScript Expression

You can put **any** JavaScript expression inside `${}`, not just variables:

```javascript
const firstName = "Kyle"

console.log(`${firstName} ${2 + 3}`) // Kyle 5
console.log(`Hello ${firstName.toUpperCase()}`) // Hello KYLE
console.log(`Random number: ${Math.random()}`) // Random number: 0.234...
```

## Multi-line Strings

Template literals also make it easy to create multi-line strings:

```javascript
const poem = `Roses are red,
Violets are blue,
Template literals are awesome,
And so are you!`

console.log(poem)
// Roses are red,
// Violets are blue,
// Template literals are awesome,
// And so are you!
```

## When to Use Template Literals

Use template literals when:

- ✅ You need to embed variables in strings
- ✅ You need multi-line strings

Stick with regular quotes when:

- ✅ You have simple, static strings with no variables

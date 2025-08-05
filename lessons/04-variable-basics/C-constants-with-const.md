---
description: Learn how to create constants using the const keyword and understand when to use const instead of let for unchanging values.
---

# `const` - Creating Constants

`const` is used to create _constant_ variables that never change their value.

## What is `const`?

`const` creates variables whose values cannot be reassigned after they're created. Think of them as permanent marker - once you set the value it cannot be changed.

```javascript
const name = "Alice"

// Trying to change a const variable will throw an error
name = "Bob" // ❌ TypeError: Assignment to constant variable
```

## Differences From `let`

1. Must Be Given a Value When Created

   Unlike `let`, you cannot create a `const` variable without giving it a value:

   ```javascript
   // ✅ Good - const with initial value
   const name = "Alice"
   const age = 45

   const message // ❌ SyntaxError: Missing initializer in const declaration
   ```

2. Cannot Be Reassigned

   Once created, you cannot change the value of a `const` variable:

   ```javascript
   const name = "Alice"

   name = "Bob" // ❌ TypeError: Assignment to constant variable
   ```

## `const` vs `let` Decision Guide

I use `const` by default unless I know the value will change. This helps prevent accidental changes to important values.

### Use `const` when:

- The value never changes
- It's a global constant like a configuration or setting

### Use `let` when:

- The value will change as your program runs
- You're counting or tracking something

## Global Constants

In larger applications, you might define global constants that are used throughout your codebase:

```javascript
const APP_NAME = "My Awesome App"
const VERSION = "1.0.0"
const SUPPORT_EMAIL = "support@example.com"
```

These global constant values are often defined in uppercase with underscores separating words.

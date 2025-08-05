---
title: Creating Variables with var
description: Learn about the var keyword and why you should avoid it in favor of let and const.
---

# Creating Variables with `var`

We've been using `let` and `const` to create variables, but there's a third option `var` that also allows you to create variables.

## What is `var`?

The `var` keyword works similarly to `let` for basic variable creation:

```javascript
var a = 1
console.log(a) // 1
a = 2
console.log(a) // 2
```

This looks identical to using `let`, but `var` behaves very differently under the hood.

### Why `var` Exists

Originally, when JavaScript was first created, `var` was the **only** way to create variables. Later, `let` and `const` were added to fix the strange and confusing behavior of `var`.

## Problems With `var`

While `var` can be used to create variables, it has several issues that make it problematic:

### `var` Uses Function Scope

The biggest issue with `var` is that it completely ignores block scope and uses function scope instead:

```javascript
function func() {
  {
    var a = 1 // Function scope
  }
  console.log(a) // Prints 1
}

func()
```

```javascript
function func() {
  {
    let a = 1 // Block scope
  }
  console.log(a) // ❌ ReferenceError: a is not defined
}

func()
```

### `var` Gets Hoisted Strangely

Variables declared with `var` get hoisted to the top of their scope, but only the declaration (not the value):

```javascript
console.log(a) // Prints undefined
var a = 1
console.log(a) // 1
```

JavaScript treats this as if you wrote:

```javascript
var a
console.log(a) // Prints undefined
a = 1 // Assignment happens here
console.log(a) // 1
```

Here is how it behaves with `let`:

```javascript
console.log(a) // ❌ ReferenceError: Cannot access 'a' before initialization
let a = 1
```

### `var` Allows Redeclaration

You can declare the same `var` variable multiple times, which can lead to confusion:

```javascript
var a = 1
var a = 2 // No error - just overwrites the first one
console.log(a) // 2
```

With `let`, you get a helpful error:

```javascript
let b = 1
let b = 2 // ❌ SyntaxError: Identifier 'b' has already been declared
```

## When You Might See `var`

1. **Older codebases** - Code written before `let` and `const` existed
2. **Legacy tutorials** - Outdated learning materials
3. **Interview questions** - Testing your understanding of JavaScript quirks

## Best Practice

- Never use `var` in modern JavaScript

The only reason to know about `var` is to understand legacy code and avoid its pitfalls when you encounter it.

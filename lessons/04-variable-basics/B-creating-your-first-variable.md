---
title: Creating Your First Variable
description: Learn how to create variables in JavaScript using the let keyword and understand how variables store values in memory.
---

# Creating Your First Variable

Variables are labeled containers that store information you want to use later in your code.

## What is a Variable?

- **Container for data** - Variables hold values like numbers, text, or other information
- **Reusable references** - Once created, you can use the variable name to access its value anywhere
- **Dynamic storage** - Variables can be updated with new values as your program runs

## Defining Variables

In JavaScript there are 3 ways to define variables, but we will focus on just one for now: `let`.

```javascript
let variableOne
let name = "Sally"
let age = 25
```

### Key Points:

- **Optional value** - You can create a variable without an initial value
- **Single equals (`=`)** assigns a value to a variable
- **Variable names** should be descriptive and meaningful
- **Case sensitive** - `age` and `Age` are different variables

## Updating Variable Values

One of the powerful features of variables is that you can change their values:

```javascript
let score = 10
console.log(score) // Prints: 10

score = 15
console.log(score) // Prints: 15

score = "name"
console.log(score) // Prints: name
```

## Benefits of Using Variables

- **Readability**: Makes your code easier to understand
- **Maintainability**: You can change values in one place without updating multiple lines
- **Reusability**: Use the same variable in different parts of your code

## Best Practices

- **Use descriptive names**: `age` instead of `a`
- **Use camelCase**: `firstName` instead of `first_name`
- **Minimize changing values**: Try to avoid changing variable values frequently, as it can make your code harder to follow

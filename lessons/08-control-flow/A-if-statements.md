---
description: Learn how to conditionally execute code using if, else if, and else statements.
---

# If Statements

If statements are one of the most fundamental concepts in programming. They allow you to run different code based on whether certain conditions are true or false.

## Basic If Statement

The simplest form of an if statement checks a condition and runs code only if that condition is true:

```javascript
const age = 18

if (age >= 18) {
  console.log("You can vote!") // This will run
}

console.log("Program continues...") // This always runs
```

The syntax is:

- `if` keyword
- Condition in parentheses `()`
- Code block in curly braces `{}`

## If...Else Statement

Use `else` to specify what happens when the condition is false:

```javascript
const age = 16

if (age >= 18) {
  console.log("You can vote!")
} else {
  console.log("You cannot vote yet") // This will run
}
```

## Multiple Conditions with Else If

Use `else if` to check multiple conditions in order:

```javascript
const temperature = 75

if (temperature > 80) {
  console.log("It's hot outside!")
} else if (temperature > 60) {
  console.log("Perfect weather!") // This will run
} else if (temperature > 40) {
  console.log("It's a bit chilly")
} else {
  console.log("It's cold!")
}
```

**Important:** Only the **first** matching condition will run, even if multiple conditions are true.

## Logical Operators

Combine multiple conditions:

### AND (`&&`) - Both conditions must be true

```javascript
const age = 25
const hasLicense = true

if (age >= 18 && hasLicense) {
  console.log("You can drive!") // Both conditions are true
}
```

### OR (`||`) - At least one condition must be true

```javascript
const isWeekend = false
const isHoliday = true

if (isWeekend || isHoliday) {
  console.log("No work today!") // One condition is true
}
```

### NOT (`!`) - Reverses the condition

```javascript
const isLoggedIn = false

if (!isLoggedIn) {
  console.log("Please log in") // This runs because !false is true
}
```

## Truthy and Falsy Values

JavaScript treats certain values as "truthy" or "falsy" in if statements:

**Falsy values** (treated as false):

- `false`
- `0`
- `""` (empty string)
- `null`
- `undefined`
- `NaN`

**Truthy values** (treated as true):

- Everything else! Including `"0"`, `[]`, `{}`

```javascript
const name = "Kyle"

if (name) {
  console.log(`Hello ${name}!`) // Runs because non-empty strings are truthy
}

const emptyString = ""
if (emptyString) {
  console.log("This won't run") // Empty strings are falsy
}
```

## Nested If Statements

You can put if statements inside other if statements:

```javascript
const weather = "sunny"
const temperature = 75

if (weather === "sunny") {
  if (temperature > 70) {
    console.log("Perfect day for the beach!") // This will run
  } else {
    console.log("Sunny but a bit cold")
  }
} else {
  console.log("Not a sunny day")
}
```

This is generally not recommended unless necessary, as it can make code harder to read.

### Guard Clauses

Guard clauses are a way to handle conditions early and exit the function or block if a condition is not met. This keeps the main logic less nested and more readable:

```javascript
const weather = "sunny"
const temperature = 75

if (weather !== "sunny") {
  console.log("Not a sunny day")
  return // Exit early
}

if (temperature > 70) {
  console.log("Perfect day for the beach!") // This will run
} else {
  console.log("Sunny but a bit cold")
}
```

## Single Line If Statements

If you have a single statement inside an if or else block, you can omit the curly braces `{}`:

```javascript
const age = 18
if (age >= 18) console.log("You can vote!") // This will run
else console.log("You cannot vote yet") // This won't run
```

I generally only use this with guard clauses since using it too often can make code harder to read.

## Exercise

Try writing an if statement that:

1. Checks if a person can get a driver's license
2. Requirements: Must be at least 16 years old AND have completed driver's education
3. If they can get a license, log "You can get your license!"
4. If they're too young, log "You must be at least 16"
5. If they haven't completed driver's ed, log "You need to complete driver's education"

<details>
<summary>Solution</summary>

```javascript
const age = 17
const hasDriversEd = true

if (age < 16) {
  console.log("You must be at least 16")
} else if (!hasDriversEd) {
  console.log("You need to complete driver's education")
} else {
  console.log("You can get your license!")
}
```

Alternative solution using guard clauses:

```javascript
const age = 17
const hasDriversEd = true
if (age < 16) {
  console.log("You must be at least 16")
  return
}

if (!hasDriversEd) {
  console.log("You need to complete driver's education")
  return
}

console.log("You can get your license!")
```

</details>

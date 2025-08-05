---
description: Learn how to use switch statements for cleaner multi-way conditional logic and how to create scoped blocks for each case.
---

# Switch Statements

Switch statements provide a cleaner way to write multiple if-else conditions when comparing a single variable against many different values.

## Basic Switch Syntax

```javascript
const favoriteAnimal = "cat"

switch (favoriteAnimal) {
  case "cat":
    console.log("Cats are pretty cool")
    break
  case "dog":
    console.log("They are kinda loud")
    break
  case "shark":
    console.log("That is an interesting choice")
    break
  default:
    console.log("That is cool but I am unfamiliar with that animal")
}
```

### How It Works

1. **Switch Expression**: The variable to check (`favoriteAnimal`).
2. **Case Labels**: Each `case` checks if the switch expression is equal to a specific value.
3. **Break Statement**: Ends the switch block after a match is found.
4. **Default Case**: Runs if no cases match, similar to `else` in if-else statements.

### Switch vs If-Else

The above switch statement is equivalent to this if-else chain:

```javascript
const favoriteAnimal = "cat"

if (favoriteAnimal === "cat") {
  console.log("Cats are pretty cool")
} else if (favoriteAnimal === "dog") {
  console.log("They are kinda loud")
} else if (favoriteAnimal === "shark") {
  console.log("That is an interesting choice")
} else {
  console.log("That is cool but I am unfamiliar with that animal")
}
```

As you can see, switch statements eliminate the repetitive `favoriteAnimal ===` checks.

## When to Use Switch vs If-Else

**Use switch when:**

- Comparing one variable against multiple specific values
- You have many conditions to check
- The conditions use strict equality (`===`)

**Use if-else when:**

- You need complex conditions (`>`, `<`, `&&`, `||`)
- Comparing different variables
- You have only a few conditions

## Advanced Features

### Multiple Cases for Same Action

If you want multiple cases to execute the same code, you can stack them on top of each other without a break between them:

```javascript
const day = "saturday"

switch (day) {
  case "monday":
  case "tuesday":
  case "wednesday":
  case "thursday":
  case "friday":
    console.log("Workday")
    break
  case "saturday":
  case "sunday":
    console.log("Weekend!") // This runs
    break
  default:
    console.log("Invalid day")
}
```

This works since a switch statement will continue running code until it hits a break statement.

### Creating Scope with Curly Braces

**Important:** Each case does **not** create its own scope by default. If you need to declare variables in a case, wrap it in curly braces:

```javascript
const action = "login"

switch (action) {
  case "login": {
    // Curly braces create a new scope
    const message = "Welcome back!"
    const timestamp = new Date()
    console.log(`${message} Login time: ${timestamp}`)
    break
  }
  case "logout": {
    // This scope is separate from the login case
    const message = "Goodbye!"
    const timestamp = new Date()
    console.log(`${message} Logout time: ${timestamp}`)
    break
  }
  case "register": {
    const message = "Account created!"
    console.log(message)
    break
  }
  default:
    console.log("Unknown action")
}
```

#### Why Scope Matters

Without curly braces, you can't redeclare variables:

```javascript
const status = "success"

switch (status) {
  case "success":
    const message = "Operation successful!" // Declares message
    console.log(message)
    break
  case "error":
    const message = "Operation failed!" // ❌ Error! Cannot redeclare 'message'
    console.log(message)
    break
}
```

With curly braces, each case has its own scope:

```javascript
const status = "success"

switch (status) {
  case "success": {
    const message = "Operation successful!" // ✅ Works
    console.log(message)
    break
  }
  case "error": {
    const message = "Operation failed!" // ✅ Works - different scope
    console.log(message)
    break
  }
}
```

## Common Mistakes

1. Forgetting Break Statements

   If you forget a `break`, the code will "fall through" to the next case:

   ```javascript
   const fruit = "apple"

   switch (fruit) {
     case "apple":
       console.log("Apple selected")
     // No break here, so it falls through
     case "banana":
       console.log("Banana selected") // This runs too!
       break
     default:
       console.log("Unknown fruit")
   }
   ```

2. Relying on Loose Equality

   Switch statements use strict equality (`===`), so be careful with types:

   ```javascript
   const value = "5"

   switch (value) {
     case 5: // ❌ This won't match because 5 is a number, not a string
       console.log("Matched number 5")
       break
     default:
       console.log("No match") // This runs
   }
   ```

3. Forgetting Scope for Variables

   If you declare variables in a case without curly braces, they will leak into the switch scope:

   ```javascript
   const action = "login"

   switch (action) {
     case "login":
       const message = "Welcome!" // Leaks to switch scope
       console.log(message)
       break
     case "logout":
       console.log(message) // ❌ Error - message is not defined here
       break
   }
   ```

   Always use curly braces to create a new scope when declaring variables in cases.

## Exercise

Create a switch statement that takes a month number (1-12) and returns the season:

- December (12), January (1), February (2): "Winter"
- March (3), April (4), May (5): "Spring"
- June (6), July (7), August (8): "Summer"
- September (9), October (10), November (11): "Fall"

<details>
<summary>Solution</summary>

```javascript
function getSeason(month) {
  switch (month) {
    case 12:
    case 1:
    case 2:
      return "Winter"
    case 3:
    case 4:
    case 5:
      return "Spring"
    case 6:
    case 7:
    case 8:
      return "Summer"
    case 9:
    case 10:
    case 11:
      return "Fall"
    default:
      return "Invalid month"
  }
}

console.log(getSeason(7)) // "Summer"
console.log(getSeason(13)) // "Invalid month"
```

</details>

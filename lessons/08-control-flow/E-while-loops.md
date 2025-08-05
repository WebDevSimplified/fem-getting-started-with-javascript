---
description: Learn how to use while loops for repeating code when you don't know exactly how many times to loop.
---

# While Loops

While loops are used when you need to repeat code, but you don't know exactly how many times the loop should run. They continue executing as long as a condition remains true.

## Basic While Loop Syntax

A while loop starts with the `while` keyword, followed by a condition in parentheses `()`, and a block of code in curly braces `{}`:

```javascript
let i = 0
while (i < 5) {
  // Code to repeat
  console.log(`Count: ${i}`)
  i++ // Important: Don't forget to change i!
}
```

The loop continues as long as the condition in parentheses is `true` and stops when it becomes `false`.

## Converting For Loop to While Loop

Here's how a for loop translates to a while loop:

```javascript
// For loop
for (let i = 0; i < 5; i++) {
  console.log(i)
}

// Equivalent while loop
let i = 0 // Initialization (outside the loop)
while (i < 5) {
  // Condition (same as for loop)
  console.log(i) // Code to run
  i++ // Increment (inside the loop)
}
```

Both print: `0, 1, 2, 3, 4`

## When to Use While Loops

1. Unknown Number of Iterations

   ```javascript
   // Keep asking for input until user enters "quit"
   let userInput = ""
   while (userInput !== "quit") {
     userInput = prompt("Enter a command (or 'quit' to exit):")
     if (userInput !== "quit") {
       console.log(`You entered: ${userInput}`)
     }
   }
   ```

2. Processing Nested Data Structures

   ```javascript
   const person = {
     name: "Kyle",
     friend: {
       name: "Joe",
       friend: {
         name: "Sally",
         friend: null, // Sally has no friend
       },
     },
   }

   // Get the final friend in the chain
   let currentPerson = person
   while (currentPerson.friend !== null) {
     currentPerson = currentPerson.friend
     console.log(`Current friend: ${currentPerson.name}`)
   }

   console.log(`Final friend: ${currentPerson.name}`) // "Final friend: Sally"
   ```

   You can't easily do this with a for loop because you don't know how deep the friend chain goes!

### While Loop vs For Loop

**Use a for loop when:**

- You know exactly how many times to loop
- You're counting or iterating through arrays
- You have a clear start, end, and increment

**Use a while loop when:**

- You don't know how many iterations you need
- You need to access nested or linked data

## Loop Control: `break` and `continue`

Just like with for loops, you can use `break` and `continue` in while loops.

## Do-While Loops

A variation that runs the code block at least once before checking the condition:

```javascript
let userInput
do {
  userInput = prompt("Enter 'yes' to continue:")
  console.log(`You entered: ${userInput}`)
} while (userInput !== "yes")
```

The key difference: `do-while` checks the condition **after** running the code block.

## Exercise

Write a while loop that simulates a simple guessing game:

1. Generate a random number between 1 and 10
2. Keep asking the user to guess until they get it right
3. Track the number of attempts
4. Give hints ("too high" or "too low")

<details>
<summary>Solution</summary>

```javascript
function guessingGame() {
  const secretNumber = Math.floor(Math.random() * 10) + 1
  let guess
  let attempts = 0

  console.log("Guess the number between 1 and 10!")

  while (guess !== secretNumber) {
    guess = parseInt(prompt("Enter your guess:"))
    attempts++

    if (guess < secretNumber) {
      console.log("Too low!")
    } else if (guess > secretNumber) {
      console.log("Too high!")
    } else {
      console.log(`Correct! You got it in ${attempts} attempts.`)
    }
  }
}
```

Alternative solution using `break`:

```javascript
function guessingGame() {
  const secretNumber = Math.floor(Math.random() * 10) + 1
  let guess
  let attempts = 0

  console.log("Guess the number between 1 and 10!")

  while (true) {
    guess = parseInt(prompt("Enter your guess:"))
    attempts++

    if (guess < secretNumber) {
      console.log("Too low!")
    } else if (guess > secretNumber) {
      console.log("Too high!")
    } else {
      console.log(`Correct! You got it in ${attempts} attempts.`)
      break
    }
  }
}
```

</details>

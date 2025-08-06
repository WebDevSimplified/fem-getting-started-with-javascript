---
description: Master the Sources tab and JavaScript debugger in Chrome DevTools for advanced debugging with breakpoints, stepping, and call stack inspection.
---

# Sources Tab and JavaScript Debugger

The Sources tab in Chrome DevTools is the most powerful tool for debugging JavaScript code. It allows you to pause execution, step through code line by line, inspect variables, and understand exactly what your program is doing at any moment. This is essential for finding complex bugs that console logging alone can't solve.

## Sources Tab Overview

The Sources tab is divided into three main panels:

1. **File Navigator** (left): Shows all files loaded by your page
2. **Code View** (center): Displays source code for the selected file
3. **Debugger Sidebar** (right): Shows scope, call stack, breakpoints, and more

## Basic Breakpoints

Breakpoints pause code execution at specific lines, allowing you to inspect the program state.

### Setting Breakpoints

You can set breakpoints by either clicking the line number where you want your code to stop in the code view or typing `debugger` in your code where you want to pause execution.

```javascript
console.log("Hi")
debugger // Execution will pause here
console.log("Bye")
```

### Managing Breakpoints

On the right sidebar, you can manage all your breakpoints under the "Breakpoints" section by toggling them on/off or removing them entirely.

#### Pausing on Exceptions

You can configure the debugger to pause when errors occur in your code.

- **Uncaught Exceptions (Always Enable)**: Pause on any error in your code that isn't handled
- **Caught Exceptions (Not Usually Needed)**: Pause on any error that is properly handled by your code

## Code Execution Control

When execution pauses at a breakpoint, you can control how the program continues. These buttons are located at the top of the right panel.

1. **Continue (F8)**: Resume normal execution until next breakpoint
2. **Step Over (F10)**: Execute current line, and skip over function calls
3. **Step Into (F11)**: Enter function calls to debug inside them
4. **Step Out (Shift+F11)**: Finish current function and return to caller
5. **Step (F9)**: Similar to Step Into, but doesn't wait for async operations

### Stepping Through Code

```javascript
function complexCalculation(a, b) {
  debugger // Pause here
  const result1 = multiply(a) // F10: Step over (don't enter multiply)
  const result2 = math(b) // F11: Step into (enter math)
  return result1 + result2 // You will pause here after stepping out of math
}

function multiply(value) {
  return value * 2
}

function math(value) {
  // If you step into this function, you'll pause here
  const doubled = value * 2
  const squared = doubled * doubled // Shift+F11: Step out (return to complexCalculation)
  return squared
}

complexCalculation(3, 4)
```

### Step vs Step Into

When you use **Step Into**, it enters the function call and pauses at the first line inside that function even if it has to wait for asynchronous code. If you use **Step**, it will execute the current line and immediately pause at the next line, skipping any asynchronous operations.

<!-- prettier-ignore -->
```javascript
debugger // Pause here
setTimeout(() => {
  console.log("Inside") // Step Into will wait 1 second and then pause here
}, 1000)

console.log("After") // Step will skip over the timeout and pause here immediately
```

## Scope and Variable Inspection

The right sidebar shows detailed information about variables and scope when execution is paused.

### Scope Panel

```javascript
window.globalVar = "I'm global"
const scriptVar = "I'm script"

function outerFunction(param1) {
  const outerVar = "I'm in outer scope"

  function innerFunction(param2) {
    const innerVar = "I'm in inner scope"

    debugger // Stop here

    return param1 + param2 + outerVar + innerVar + globalVar
  }

  return innerFunction("inner param")
}

outerFunction("outer param")
```

**When paused, the Scope panel shows:**

- **Local**: Variables in current function (`innerVar`, `param2`)
- **Closure**: Variables from outer scopes (`outerVar`, `param1`)
- **Script**: Global variables (`scriptVar`)
- **Global**: Variables attached to the `window` object (`globalVar`)

### Inspecting Variables

When paused you can hover over any variable in your code to see its current value.

#### Watch expressions

The Watch panel allows you to monitor specific variables or expressions continuously by entering any expression you want to track.

#### Console evaluation

While paused you can run code in the console that has access to the current scope. This is useful for testing fixes or inspecting values without modifying your code.

## Call Stack Analysis

The Call Stack panel shows the sequence of function calls that led to the current point. This is the same as the "stack trace" you see in error messages, but you can explore it interactively by clicking on any function in the stack to jump to that point in the code.

## Advanced Breakpoints

There are many advanced breakpoint types you can use to pause execution under specific conditions

### DOM Breakpoints

You can set breakpoints that pause execution when specific DOM elements change. This is useful for debugging dynamic web applications.

- **Subtree modifications**: Child elements added/removed
- **Attributes modifications**: Attributes changed on current element
- **Node removal**: Element itself removed

You set these by right-clicking an element in the Elements tab and selecting "Break on...".

### Event Listener Breakpoints

Similar to DOM breakpoints, you can pause execution when specific events trigger event listeners. This is useful for debugging user interactions.

1. In Sources tab on the right panel, expand "Event Listener Breakpoints"
2. Check event categories you want to debug:
   - Mouse events (click, mouseover, etc.)
   - Keyboard events
   - Form events
   - Timer events
   - etc.

```javascript
// This will pause if "Mouse → click" breakpoint is enabled
document.addEventListener("click", (event) => {
  console.log("Clicked:", event.target)
})

// This will pause if "Timer → setInterval fired" is enabled
setInterval(() => {
  console.log("Timer fired")
}, 1000)
```

### Conditional Breakpoints

You can set breakpoints that only pause when a specific condition is true. This is useful for debugging complex logic without stopping on every iteration.

To do this just right-click the line number where you want to set the breakpoint and select "Add Conditional Breakpoint". Then enter your condition.

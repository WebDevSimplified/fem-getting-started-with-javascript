---
description: Learn how to make your web pages interactive by adding event listeners to respond to user actions like clicks, form submissions, and more.
---

# Event Listeners

Event listeners are what make web pages interactive. They allow you to respond to user actions like clicks, keyboard input, form submissions, and much more.

## What Are Events?

Events are things that happen in the browser - a user clicks a button, types in an input field, submits a form, resizes the window, etc. Event listeners are functions that "listen" for these events and run code when they occur.

## Basic Event Listener Syntax

To add an event listener to an element, use the `addEventListener` method:

```javascript
const button = document.querySelector("button")
button.addEventListener("click", () => {
  console.log("Button was clicked!")
})
```

The `addEventListener` method takes two main arguments:

- **eventType**: A string representing the type of event (e.g., "click", "input", "submit")
- **function**: The function to run when the event occurs

## Adding Event Listeners to Elements

You can add event listeners to any DOM element:

```javascript
const input = document.querySelector("input")
input.addEventListener("input", (e) => {
  console.log("Input value:", e.target.value)
})

document.addEventListener("click", () => {
  console.log("Document was clicked")
})

window.addEventListener("resize", () => {
  console.log("Window resized to:", window.innerWidth, window.innerHeight)
})
```

### Multiple Event Listeners

You can add multiple event listeners to the same element:

```javascript
const button = document.querySelector("[data-button]")

button.addEventListener("click", () => {
  console.log("First listener")
})

button.addEventListener("click", () => {
  console.log("Second listener")
})

// When clicked, both will run:
// "First listener"
// "Second listener"
```

Event listeners never overwrite each other and always run in the order they were added to the element.

## Removing Event Listeners

To remove an event listener, you need a reference to the exact same function:

```javascript
// ✅ This works - named function
function handleClick() {
  console.log("Clicked!")
}

const button = document.querySelector("button")

// Add the listener
button.addEventListener("click", handleClick)

// Remove the listener
button.removeEventListener("click", handleClick)
```

```javascript
// ❌ This doesn't work - different function objects
button.addEventListener("click", () => {
  console.log("Clicked!")
})

// This creates a NEW function, so it won't remove the first one
button.removeEventListener("click", () => {
  console.log("Clicked!")
})
```

## The Event Object

Event listener functions automatically receive an **event object** that contains information about the event:

```javascript
button.addEventListener("click", (event) => {
  console.log(event) // MouseEvent object with lots of info
})
```

### Common Event Object Properties

```javascript
button.addEventListener("click", (e) => {
  // The element that triggered the event
  console.log(e.target) // The button element

  // The element the listener is attached to
  console.log(e.currentTarget) // The button element

  // Mouse position (for mouse events)
  console.log(e.clientX, e.clientY) // X and Y coordinates

  // Modifier keys
  console.log(e.ctrlKey) // true if Ctrl was held
  console.log(e.shiftKey) // true if Shift was held
  console.log(e.altKey) // true if Alt was held
})
```

### `target` vs `currentTarget`

- **`target`** - The actual element that triggered the event (could be a child element)
- **`currentTarget`** - The element the event listener is attached to

```javascript
document.addEventListener("click", (e) => {
  console.log(e.target) // The specific element clicked
  console.log(e.currentTarget) // Always the document
})
```

Generally, `currentTarget` is what you want when working inside an event listener since it refers to the element you added the listener to.

## Common Event Types

Memorizing [all event types](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Events) is impossible, but here are some of the most commonly used ones:

### Mouse Events

- `click` - When an element is clicked
- `dblclick` - When an element is double-clicked
- `mouseenter` - When the mouse enters an element
- `mouseleave` - When the mouse leaves an element
- `mouseover` - When the mouse moves over an element (fires continuously)

### Focus Events

- `focus` - When an element (like an input) receives focus
- `blur` - When an element loses focus

### Input Events

- `input` - Fires every time the value of an input changes (typing, pasting, etc.)
- `change` - Fires when the input loses focus and its value has changed

### Window Events

- `resize` - When the window is resized

You can add any event listener to the `window` object, but the only one you will commonly use is `resize` since it doesn't work on any other element.

## Preventing default behavior - `preventDefault`

Many events have default browser behavior associated with them. For example, clicking a link navigates to a new page, submitting a form redirects you to the form action, etc.

```html
<form>
  <input type="text" name="username" placeholder="Username" required />
  <button type="submit">Submit</button>
</form>
```

```javascript
const form = document.querySelector("form")

form.addEventListener("submit", (e) => {
  // Prevent the default form submission behavior
  e.preventDefault()

  console.log("Form submitted!")

  // Now you can handle the form data yourself
  const formData = new FormData(e.currentTarget)
  const username = formData.get("username")
  console.log("Username:", username)
})
```

```javascript
// Prevent links from navigating
const link = document.querySelector("a")
link.addEventListener("click", (e) => {
  e.preventDefault()
  console.log("Link clicked but navigation prevented")
})

// Prevent context menu (right-click menu)
document.addEventListener("contextmenu", (e) => {
  e.preventDefault()
  console.log("Right-click menu prevented")
})
```

## Common Mistakes

1. Accidentally Calling the Function

   ```javascript
   function handleClick() {
     console.log("Button clicked")
   }

   // ❌ Wrong - calling the function immediately
   button.addEventListener("click", handleClick())

   // ✅ Correct - passing the function reference
   button.addEventListener("click", handleClick)
   ```

2. Using `target` instead of `currentTarget`

   ```html
   <button>
     <span>Click Me</span>
   </button>
   ```

   ```javascript
   button.addEventListener("click", (e) => {
     // ❌ Wrong - target is most likely the <span> element
     console.log(e.target)

     // ✅ Correct - currentTarget is always the button
     console.log(e.currentTarget)
   })
   ```

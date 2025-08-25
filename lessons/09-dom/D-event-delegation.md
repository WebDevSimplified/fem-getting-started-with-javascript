---
description: Learn about event delegation, event bubbling, and event capturing - powerful concepts that allow you to handle events efficiently and work with dynamically added elements.
---

# Event Delegation

Event delegation is a JavaScript feature that passes events from child elements to a parent element, allowing you to handle events more efficiently and work with dynamically added elements.

## Understanding Event Flow

Before we dive into event delegation, we need to understand how events flow through the DOM. When you click on an element, you're actually clicking on multiple elements at once!

```html
<html>
  <body>
    <div class="container">
      <button>Click Me</button>
    </div>
  </body>
</html>
```

When you click the button, you're also clicking on:

- The `div` container (the button is inside it)
- The `body` element (the div is inside it)
- The `html` element (the body is inside it)
- The `document` (everything is inside it)

### Event Flow Phases

Events flow through the DOM in three phases:

- **Phase 1 - Capture**: The event travels from the document down to the target element
- **Phase 2 - Target**: The event reaches the actual target element
- **Phase 3 - Bubble**: The event travels back up from the target to the document

## Seeing Event Bubbling in Action

By default events trigger in the bubble phase, meaning they start at the target element and bubble up to its ancestors.

```html
<div id="outer">
  <div id="middle">
    <button id="inner">Click Me</button>
  </div>
</div>
```

```javascript
const outer = document.querySelector("#outer")
const middle = document.querySelector("#middle")
const inner = document.querySelector("#inner")

outer.addEventListener("click", () => {
  console.log("Outer div clicked")
})

middle.addEventListener("click", () => {
  console.log("Middle div clicked")
})

inner.addEventListener("click", () => {
  console.log("Button clicked")
})

// When you click the button, you'll see:
// "Button clicked"
// "Middle div clicked"
// "Outer div clicked"
```

The event starts at the button (target) and bubbles up through its ancestors.

## Controlling Event Flow

You may not want this default bubbling behavior, so there are a few ways to control it:

### Stopping Event Propagation - `stopPropagation`

You can stop an event from propagating to other elements by calling `stopPropagation()` on the event object:

```html
<div id="outer">
  <div id="middle">
    <button id="inner">Click Me</button>
  </div>
</div>
```

```javascript
inner.addEventListener("click", (e) => {
  console.log("Button clicked")
  e.stopPropagation() // Stop the event here!
})

middle.addEventListener("click", () => {
  console.log("This won't run!")
})

outer.addEventListener("click", () => {
  console.log("This won't run either!")
})

// When you click the button, you'll see:
// "Button clicked"
```

### Capture Phase Event Listeners

By default, event listeners run during the bubble phase, but you can make them run during the capture phase instead:

```html
<div id="outer">
  <button id="inner">Click Me</button>
</div>
```

```javascript
// This runs during the CAPTURE phase (document → target)
outer.addEventListener(
  "click",
  () => {
    console.log("Outer div clicked (capture)")
  },
  { capture: true }
)

// This runs during the BUBBLE phase (target → document)
inner.addEventListener("click", () => {
  console.log("Button clicked (bubble)")
})

// When clicking the button, you'll see:
// "Outer div clicked (capture)"
// "Button clicked (bubble)"
```

### When To Use Each Phase

By default you should use the bubble phase for most event listeners, but the capture phase can be useful if you want to stop an event before it reaches the target element.

```html
<div id="outer">
  <button id="inner">Click Me</button>
</div>
```

```javascript
outer.addEventListener(
  "click",
  (e) => {
    e.stopPropagation() // Stop the event from reaching the target
  },
  { capture: true }
)

inner.addEventListener("click", () => {
  console.log("This never runs!")
})
```

### Not All Events Can Be Delegated

Pretty much all events go through the normal bubble/capture phases, but some events don't bubble up. `focus` and `blur` are the most common events that do not bubble.

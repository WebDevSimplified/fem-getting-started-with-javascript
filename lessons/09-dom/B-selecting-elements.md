---
description: Learn different ways to select HTML elements in JavaScript, including getElementById, getElementsByClassName, and the powerful querySelector methods.
---

# Selecting Elements

One of the most fundamental skills in web development is selecting HTML elements so you can interact with them using JavaScript. There are several methods available, each with their own strengths and use cases.

## Method 1: `getElementById`

The `getElementById` method selects a single element based on its ID attribute.

```html
<div id="header">This is a header</div>
```

```javascript
const header = document.getElementById("header")
console.log(header) // <div id="header">This is a header</div>

// Change the text color
header.style.color = "blue"
```

### Key Points about getElementById:

- Returns a **single element** (or `null` if not found)
- IDs should be unique on a page
- You only pass the ID name, not `#header`
- Fast and efficient

```javascript
// ❌ Wrong - don't include the #
const wrong = document.getElementById("#header")

// ✅ Correct - just the ID name
const correct = document.getElementById("header")
```

## Method 2: `getElementsByClassName`

The `getElementsByClassName` method selects multiple elements based on their class name.

```html
<div class="content">First content div</div>
<div class="content">Second content div</div>
<div class="content">Third content div</div>
```

```javascript
const contentDivs = document.getElementsByClassName("content")
console.log(contentDivs) // HTMLCollection with 3 elements

// This is an HTMLCollection, not an array!
console.log(contentDivs.length) // 3
console.log(contentDivs[0]) // First content div
```

### Working with HTMLCollections

HTMLCollections look like arrays but don't have all array methods:

```javascript
const contentDivs = document.getElementsByClassName("content")

// ❌ This won't work - HTMLCollection doesn't have forEach
// contentDivs.forEach(div => console.log(div))

// ✅ Convert to array first
const contentArray = Array.from(contentDivs)
contentArray.forEach((div) => {
  div.style.color = "green"
})

// ✅ Or use a regular for loop
for (let i = 0; i < contentDivs.length; i++) {
  contentDivs[i].style.backgroundColor = "lightgray"
}

// ✅ Or access individual elements by index
contentDivs[0].style.fontWeight = "bold"
```

## Method 3: `querySelector` (Recommended)

The `querySelector` method uses CSS selectors to find elements. It returns the **first** matching element.

```html
<div id="header">This is a header</div>
<div class="content">First content div</div>
<div class="content">Second content div</div>
<button data-action="submit">Submit</button>
```

```javascript
// Select by ID (same as getElementById)
const header = document.querySelector("#header")
console.log(header) // <div id="header">This is a header</div>

// Select by class (gets first element with that class)
const firstContent = document.querySelector(".content")
console.log(firstContent) // <div class="content">First content div</div>

// Select by tag name
const firstDiv = document.querySelector("div")
console.log(firstDiv) // <div id="header">This is a header</div>

// Select by attribute
const submitButton = document.querySelector('[data-action="submit"]')
console.log(submitButton) // <button data-action="submit">Submit</button>
```

## Method 4: `querySelectorAll` (Recommended)

The `querySelectorAll` method returns **all** matching elements as a NodeList.

```html
<div id="header">This is a header</div>
<div class="content">First content div</div>
<div class="content">Second content div</div>
<div class="content">Third content div</div>
<input type="text" name="username" placeholder="Enter username" />
```

```javascript
// Get all elements with class "content"
const allContent = document.querySelectorAll(".content")
console.log(allContent) // NodeList with 3 elements

// Get all divs
const allDivs = document.querySelectorAll("div")
console.log(allDivs) // NodeList with 4 elements

// Get all inputs
const allInputs = document.querySelectorAll("input")
console.log(allInputs) // NodeList with 1 element
```

### Working with NodeLists

NodeLists look like arrays (similar to HTMLCollections) but lack some array methods. However, they do have `forEach`:

```javascript
// ✅ This works - NodeList has forEach
const allContent = document.querySelectorAll(".content")

allContent.forEach((div) => {
  div.style.padding = "10px"
})
```

## Live vs Static Collections

The biggest difference between the `querySelectorAll` and `getElementsByClassName` methods is that `getElementsByClassName` returns a **live** HTMLCollection, while `querySelectorAll` returns a **static** NodeList.

This means that if the DOM changes after you select elements with `getElementsByClassName`, the HTMLCollection will automatically update to reflect those changes. In contrast, a NodeList from `querySelectorAll` will not change unless you call `querySelectorAll` again.

```html
<div class="content">First content div</div>
<div class="content">Second content div</div>
<div class="content">Third content div</div>
```

```javascript
// Using getElementsByClassName (live)
const liveCollection = document.getElementsByClassName("content")
console.log(liveCollection.length) // 3

// Add a new content div
const newDiv = document.createElement("div")
newDiv.className = "content"
document.body.appendChild(newDiv)

console.log(liveCollection.length) // 4 (updates automatically)
```

```javascript
// Using querySelectorAll (static)
const staticNodeList = document.querySelectorAll(".content")
console.log(staticNodeList.length) // 3

// Add a new content div
const newDiv = document.createElement("div")
newDiv.className = "content"
document.body.appendChild(newDiv)

console.log(staticNodeList.length) // 3 (remains the same)
```

In almost all cases a live collection is not wanted since it makes your code more difficult to understand and less predictable.

## When to Use Each Method

By default you should prefer `querySelector` and `querySelectorAll` for pretty much everything. They are more flexible, use familiar CSS selector syntax, and return a static NodeList.

You can use `getElementById` when you need to select a single element by ID and want the absolute best performance since it is marginally faster than `querySelector`.

## Using Advanced CSS Selectors

`querySelector`/`querySelectorAll` accept any valid CSS selector:

```javascript
// Attribute selectors
document.querySelector('input[name="username"]')
document.querySelector('img[alt*="logo"]')
document.querySelectorAll('a[href^="https://"]')

// Pseudo-selectors
document.querySelector("li:first-child")
document.querySelector("tr:nth-child(even)")
document.querySelector("input:checked")
document.querySelector("div:not(.hidden)")

// Combinators
document.querySelector("nav > ul > li") // Direct child
document.querySelector("h2 + p") // Adjacent sibling
document.querySelector("article p") // Descendant

// Multiple selectors
document.querySelector("button, input[type='submit']") // Either one
```

## Exercise

Given this HTML, write JavaScript to:

1. Change the header text to "Welcome!"
2. Make all paragraphs blue
3. Hide the last paragraph
4. Add a border to inputs with the "required" class

```html
<h1 id="main-header">Original Header</h1>
<p class="text">First paragraph</p>
<p class="text">Second paragraph</p>
<p class="text">Third paragraph</p>
<input type="text" class="required" placeholder="Name" />
<input type="email" class="required" placeholder="Email" />
<input type="tel" placeholder="Phone" />
```

- You can use `style.property` to change CSS styles, e.g. `element.style.color = "red"`.
- You can use `textContent` to change text, e.g. `element.textContent = "New Text"`.

<details>
<summary>Solution</summary>

```javascript
// 1. Change header text
document.querySelector("#main-header").textContent = "Welcome!"

// 2. Make all paragraphs blue
document.querySelectorAll("p").forEach((p) => {
  p.style.color = "blue"
})

// 3. Hide the last paragraph
const lastParagraph = document.querySelector("p:last-child")
lastParagraph.style.display = "none"

// 4. Add border to required inputs
document.querySelectorAll("input.required").forEach((input) => {
  input.style.border = "2px solid red"
})
```

</details>

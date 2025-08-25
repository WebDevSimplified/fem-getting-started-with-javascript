---
title: DOM Traversal
description: Learn how to navigate through the DOM tree using JavaScript to move from one element to related elements like parents, children, and siblings.
---

# DOM Traversal

DOM traversal is the process of navigating through the DOM tree structure to move from one element to related elements. Instead of selecting elements by their IDs or classes every time, you can start with one element and traverse to its parents, children, or siblings.

## Understanding the DOM Tree Structure

The DOM is structured like a family tree. Every element has relationships with other elements:

```html
<div id="grandparent">
  <div id="parent-1">
    <div id="child-1">Child 1</div>
    <div id="child-2">Child 2</div>
  </div>
  <div id="parent-2">Parent 2</div>
</div>
```

### Visual Representation

```text
grandparent
├── parent-1
│   ├── child-1
│   └── child-2
└── parent-2
```

In this structure:

- `grandparent` is the **parent** of `parent-1` and `parent-2`
- `parent-1` and `parent-2` are **siblings** (they share the same parent)
- `child-1` and `child-2` are **children** of `parent-1`
- `child-1` and `child-2` are **siblings** of each other

## Traversing to Child Elements

The `children` property returns a **live HTMLCollection** of all direct child elements:

```html
<div id="grandparent">
  <div id="parent-1">Parent 1</div>
  <div id="parent-2">Parent 2</div>
</div>
```

```javascript
const grandparent = document.querySelector("#grandparent")
const children = grandparent.children

console.log(children) // HTMLCollection with parent-1 and parent-2
console.log(children.length) // 2

// Access individual children by index
const firstChild = children[0] // parent-1
const secondChild = children[1] // parent-2
```

### Getting Specific Children

You can use `querySelector` and `querySelectorAll` on any element, not just `document`:

```html
<div id="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <span class="item">Item 3</span>
</div>
```

```javascript
const container = document.querySelector("#container")

// Find all elements with class "item" inside the container
const items = container.querySelectorAll(".item")
console.log(items.length) // 3

// Find the first div with class "item" inside the container
const firstDiv = container.querySelector("div.item")
console.log(firstDiv.textContent) // "Item 1"
```

## Traversing to Sibling Elements

`nextElementSibling` and `previousElementSibling` allow you to move between sibling elements at the same level in the DOM tree.

```html
<div id="one">1</div>
<div id="two">2</div>
<div id="three">3</div>
```

```javascript
const two = document.querySelector("#two")
const three = two.nextElementSibling
const one = two.previousElementSibling
```

### What About `nextSibling` and `previousSibling`?

`nextSibling` and `previousSibling` may seem like they do the same thing, but they return **any** node, including text nodes (like whitespace):

```html
<div id="one">1</div>
<div id="two">2</div>
<div id="three">3</div>
```

```javascript
const two = document.querySelector("#two")
const three = two.nextSibling
const one = two.previousSibling

console.log(three) // Grabs the text between divs (whitespace)
console.log(one) // Grabs the text between divs (whitespace)
```

## Traversing to Parent Elements

`parentElement` allows you to move up the DOM tree to the parent of an element:

```html
<div id="grandparent">
  <div id="parent-1">
    <div id="child-1">Child 1</div>
  </div>
  <div id="parent-2">Parent 2</div>
</div>
```

```javascript
const child1 = document.querySelector("#child-1")
const parent1 = child1.parentElement

console.log(parent1.id) // "parent-1"

// Chain to go up multiple levels
const grandparent = child1.parentElement.parentElement

console.log(grandparent.id) // "grandparent"
```

### Don't Use `parentNode`

Just like `nextSibling`, `parentNode` can return nodes that are not elements. Always prefer `parentElement` for traversing up the DOM tree.

### Finding Ancestors: `closest()`

The `closest()` method is incredibly useful - it searches up the DOM tree for the first ancestor that matches a CSS selector:

```html
<div class="container">
  <div class="section">
    <div class="card">
      <button id="delete-btn">Delete</button>
    </div>
  </div>
</div>
```

```javascript
const deleteBtn = document.querySelector("#delete-btn")

// Find the closest ancestor with class "card"
const card = deleteBtn.closest(".card")

// Find the closest ancestor with class "section"
const section = deleteBtn.closest(".section")

// Find the closest ancestor with class "container"
const container = deleteBtn.closest(".container")

// If no matching ancestor is found, returns null
const nonExistent = deleteBtn.closest(".does-not-exist")
console.log(nonExistent) // null
```

## Prefer `closest` and `querySelector` Over Other Methods

If you use `children`, `nextElementSibling`, `previousElementSibling`, and `parentElement` too much, your code can become brittle and break if the HTML structure changes.

Instead, prefer `closest` and `querySelector`/`querySelectorAll` to find elements based on their relationships and CSS selectors. This makes your code more flexible and easier to maintain.

```html
<div class="post">
  <h2 class="post-title">My First Post</h2>
  <p class="post-content">This is the content of my first post.</p>
  <button class="edit-btn">Edit</button>
</div>
```

```javascript
const editBtn = document.querySelector(".edit-btn")
editBtn.addEventListener("click", () => {
  // This works, but is brittle if HTML structure changes
  const post = editBtn.parentElement
  const title = post.children[0]
  console.log(title) // <h2 class="post-title">My First Post</h2>
})
```

Now imagine if we changed the HTML structure:

```html
<div class="post">
  <h2 class="post-title">My First Post</h2>
  <p class="post-content">This is the content of my first post.</p>
  <div class="actions">
    <button class="edit-btn">Edit</button>
  </div>
</div>
```

Our original code would break because `editBtn.parentElement` is no longer the `.post` element.

```javascript
const editBtn = document.querySelector(".edit-btn")
editBtn.addEventListener("click", () => {
  // This works, but is brittle if HTML structure changes
  const post = editBtn.closest(".post")
  const title = post.querySelector(".post-title")
  console.log(title) // <h2 class="post-title">My First Post</h2>
})
```

By using `closest` and `querySelector`, our code can adapt to changes in the HTML structure without breaking.

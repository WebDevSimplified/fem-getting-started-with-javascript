---
description: Learn about the window and document objects - the foundation for interacting with web pages in JavaScript.
---

# Window and Document Objects

When JavaScript runs in a browser, it has access to two fundamental global objects: `window` and `document`. Understanding these objects is essential for web development, as they provide the interface between your JavaScript code and the web page.

## The Window Object

The `window` object represents the browser window and serves as the **global object** for all JavaScript running in that window. Everything you access globally is actually a property of the window object.

### Understanding the Global Nature of Window

```javascript
// These are equivalent:
console.log("Hello")
window.console.log("Hello")

// Same with other global functions:
alert("Hi there!")
window.alert("Hi there!")
```

When you use any global function or variable, JavaScript automatically assumes you mean `window.something`.

### Exploring the Window Object

```javascript
console.log(window)
```

If you run this in your browser console, you'll see that the window object contains an enormous amount of properties and methods, but you don't need to worry about memorizing them all.

### When You Actually Need to Use `window`

Most of the time, you don't need to explicitly write `window.` because JavaScript assumes it. However, there are some cases where you need to use it:

1. Conflicting Names

   If you have a variable or function with the same name as a global property, you need to use `window` to access the global version.

   ```javascript
   // If you create a variable with the same name as a global function
   const alert = "This is my custom alert message"

   // This won't work - it tries to use your variable as a function
   // alert("Hello") // ❌ Error

   // But this will work - explicitly uses the window's alert function
   window.alert(alert) // ✅ Shows: "This is my custom alert message"
   ```

2. Creating Global Variables

   If you want to create a global variable that can be accessed in any script, you can assign it directly to `window`:

   ```javascript
   window.myGlobalVar = "Hello, World!"
   console.log(myGlobalVar) // ✅ "Hello, World!"
   ```

   I would generally recommend against creating global variables, though, as they make your code harder to maintain.

## The Document Object

The `document` object represents the HTML document loaded in the window. The HTML of your page is often referred to as the **DOM** (Document Object Model).

### What is the Document Object?

```javascript
console.log(document)
```

When you log the document object, you'll see it contains the entire HTML structure of your page - from the `<!DOCTYPE html>` declaration all the way down to the closing `</html>` tag.

The document object is actually just a property of window:

```javascript
// These are equivalent:
console.log(document)
console.log(window.document)
```

### Key Document Properties

```javascript
// Get the entire HTML element
console.log(document.documentElement) // The <html> element

// Get the body element
console.log(document.body) // The <body> element

// Get the head element
console.log(document.head) // The <head> element

// Get the current URL
console.log(document.URL)
```

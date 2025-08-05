---
title: "Your First JavaScript App"
description: "Setting up your development environment and writing your very first JavaScript program."
---

# Your First JavaScript App

Let's write your very first JavaScript program! We'll create the classic "Hello World" application.

## Setting Up Your Workspace

1. Open VS Code
2. Create a Project Folder
   - Click **File** → **Open Folder**
   - Choose or create a new folder for your project

### VS Code Layout

Once your folder is open, you'll see:

- **Left sidebar**: File explorer
- **Center**: Code editor
- **Bottom**: Terminal (we'll use this to run code)

### Important Keyboard Shortcuts

- **Toggle Sidebar**: `Ctrl + B`
- **Toggle Terminal**: `Ctrl + ~`
- **Save File**: `Ctrl + S`

## Creating Your First JavaScript App

### 1. Create a File

- Click the **New File** button in the sidebar
- Name it: `script.js`
- The `.js` extension tells VS Code this is JavaScript

### 2. Write Your First Code

In `script.js`, type exactly this:

```javascript
console.log("Hello World")
```

### 3. Save the File

- The white dot next to filename disappears when saved

## Running Your Code

### Node.js

1. Open Terminal
2. Run the command `node script.js`

**Result:** You'll see "Hello World" printed in the terminal!

#### Quick Tip

- Press **Up Arrow** to rerun the last command

### Browser

1. Create an `index.html` HTML File

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <meta charset="UTF-8" />
       <meta name="viewport" content="width=device-width, initial-scale=1.0" />
       <title>My First App</title>
       <script src="script.js"></script>
     </head>
     <body>
       <h1>My First JavaScript App</h1>
     </body>
   </html>
   ```

2. Open With Live Server
3. View JavaScript Output
   - Right-click on the webpage
   - Select **"Inspect"** (or press `Ctrl + Shift + I`)
   - Click the **"Console"** tab
   - You'll see "Hello World" printed there!

## Common Mistakes

### Missing Quotes

```javascript
// ❌ Wrong
console.log(Hello World);

// ✅ Correct
console.log('Hello World');
```

### Missing Parentheses

```javascript
// ❌ Wrong
console.log'Hello World';

// ✅ Correct
console.log('Hello World');
```

### Typos in console.log

```javascript
// ❌ Wrong
consol.log("Hello World")

// ✅ Correct
console.log("Hello World")
```

## Comments In JavaScript

Comments can be added to your code to make it easier to understand. They are ignored by the JavaScript engine.

### Single-line Comments

Use `//` to add a comment on a single line:

```javascript
// This is a single-line comment
console.log("Hello World") // This will print "Hello World"
```

### Multi-line Comments

Use `/* ... */` to add comments that span multiple lines:

```javascript
/*
  This is a multi-line comment
  It can span multiple lines
*/
console.log("Hello World")
```

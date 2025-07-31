---
description: "Installing and using the Live Server extension for faster web development."
---

## What Is Live Server?

Live Server creates a local development server and **automatically refreshes** your browser when you save changes to your files.

### Without Live Server 😩

1. Write code
2. Save file
3. Switch to browser
4. Manually refresh page
5. Switch back to VS Code
6. Repeat for every change

### With Live Server 🎉

1. Write code
2. Save file
3. **Page automatically updates!**

## Installing Live Server

1. Click the **Extensions** button in VS Code
2. Search for "**Live Server**"
3. Install the one with tens of millions of downloads (by Ritwick Dey)

### Alternatively:

1. Launch VSCode Quick Open `Ctrl+P`
2. Run `ext install ritwickdey.liveserver`

## Using Live Server

### 1. Create an HTML File

You need at least one `.html` file in your project to use Live Server.

Example `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Website</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```

### 2. Start Live Server

**Method 1: Right-click**

- Right-click your HTML file in the sidebar
- Select **"Open with Live Server"**

**Method 2: Status bar**

- Look for "Go Live" button in bottom status bar
- Click it to start Live Server

### 3. View in Browser

- Live Server automatically opens your default browser
- Shows your webpage at `http://127.0.0.1:5500`

## Live Server in Action

1. Make any change to your HTML, CSS, or JavaScript
2. Save the file
3. **Browser automatically refreshes!**
4. See your changes instantly

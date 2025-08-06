---
description: Learn to use Chrome DevTools effectively for debugging JavaScript, including the Elements, Console, Network, and Performance tabs.
---

# Browser DevTools Basics

The browser DevTools are one of the most powerful debugging tools available to JavaScript developers. They're built right into your browser and provide everything you need to inspect, debug, and optimize your web applications. Let's explore the essential features every developer should know.

_The specific features of this page are focused on Chrome's devtools, but the general concepts apply to other browsers as well._

## Opening DevTools

There are several ways to open your DevTools:

1. Keyboard Shortcuts

   - **Windows/Linux**: `F12` or `Ctrl + Shift + I`
   - **Mac**: `Cmd + Option + I`

2. Right-Click Method

   - Right-click on any element and select "Inspect"
   - This opens DevTools with the element highlighted in the Elements tab

3. Chrome Menu

   - Click the three dots menu → More Tools → Developer Tools

### DevTools Overview

When the DevTools open, you'll see several tabs across the top. The most important ones for beginners are:

1. **Elements** - View and edit HTML/CSS
2. **Console** - JavaScript console for running code and viewing logs/errors
3. **Network** - Monitor network requests
4. **Application** - View local storage, cookies, and other data
5. **Sources** - View source files and debug code line by line
6. **Performance** - Analyze page performance and resource usage

## The Elements Tab

The Elements tab shows you the HTML structure of your page and lets you inspect and modify it in real-time.

### Key Features

1. HTML Structure Navigation

   - Expand/collapse elements with the arrow icons
   - Elements are nested to show the DOM hierarchy
   - Hover over elements in DevTools to highlight them on the page

2. Live HTML Editing

   - Double-click on any text to edit it
   - Right-click elements for options:
     - Edit as HTML
     - Delete element
     - Copy element
     - Hide element

3. Styles Panel

   The right side shows CSS styles for the selected element which you can add to or modify:

   **Styles panel features:**

   - **Computed tab**: Shows final computed styles
   - **Styles tab**: Shows CSS rules and their sources
   - **Live editing**: Click on any CSS value to edit it
   - **Color picker**: Click on color values to use the color picker
   - **Box model**: Visual representation of margin, border, padding

4. Event Listeners

   Click "Event Listeners" tab to see JavaScript events attached to an element. This tab sometimes shows too many events and can be hard to parse important information from.

5. Force CSS States

   You can simulate different CSS states like `:hover`, `:active`, and `:focus`:

   - Right-click on an element → Force state
   - Select the state you want to simulate
   - This is useful for testing hover effects without needing to actually hover over the element

### Practical Examples

Let's look at some practical examples of using the Elements tab.

#### Example 1: Debugging Layout Issues

```html
<!-- Your element isn't showing up as expected -->
<div class="header">
  <h1>My Title</h1>
</div>
```

**Using Elements tab to debug:**

1. Right-click on the element → Inspect
2. Check the Styles panel for:
   - `display: none` (element is hidden)
   - `visibility: hidden` (element is invisible)
   - Width/height values of 0
   - Margin/padding issues
3. Edit CSS values directly to test fixes

#### Example 2: Finding CSS Conflicts

```css
/* Multiple CSS rules affecting the same element */
.btn {
  color: blue;
}
.primary {
  color: red;
}
.button-override {
  color: green !important;
}
```

**In the Styles panel:**

- Crossed-out styles show what's been overridden
- Source file and line numbers are shown

## The Console Tab

The Console is where all your logs/errors appear and where you can run JavaScript commands directly. We will cover logging in depth on the next page, so this section will be very brief.

### Running JavaScript

You can execute JavaScript directly in the Console:

```javascript
// Try these in the Console:
document.title = "New Title"
document.body.style.backgroundColor = "lightblue"

// Get elements
const button = document.querySelector("button")
button.style.fontSize = "20px"

// Test functions
function add(a, b) {
  return a + b
}
add(5, 3) // Returns 8
```

_You may get a warning in the console telling you that pasting information into the console can be dangerous. Just type `allow pasting` into the console and press enter to allow it._

## The Network Tab

The Network tab shows all network requests your page makes (HTML, CSS, JavaScript, images, API requests, etc.).

### Key Features

1. Request Monitoring

   - Shows all HTTP requests
   - Status codes (200 = success, 404 = not found, 500 = server error)
   - Response times
   - File sizes

2. Filtering

   - Filter by type: JS, CSS, Img, Media, Font, Doc, WS, Other
   - Filter by status code
   - Search for specific files

3. Request Details

   Click on any request to see:

   - **Headers**: Request and response headers
   - **Preview**: Formatted view of the response
   - **Response**: Raw response data
   - **Timing**: Detailed timing breakdown

### Important Options

- **Preserve log**: Keep requests after page reload
- **Disable cache**: Bypass cache (I almost always have this enabled)
- **Throttle**: Simulate slow network conditions

## The Application Tab

The Application tab lets you inspect data stored on your browser. The 3 main types of storage are:

1. **Local Storage** - Key-value pairs stored in the browser
2. **Session Storage** - Similar to local storage, but data is cleared when the tab is closed
3. **Cookies** - Small pieces of data sent by the server and stored in the browser

### Viewing and Editing Storage

1. Look in "Storage" in the left sidebar
2. Click on "one of the storage options" → your domain
3. See all stored data
4. Double-click values to edit them
5. Right-click to delete entries

## The Sources Tab

The Sources tab shows all the files loaded by your page (HTML, CSS, JavaScript, etc.). This tab is very useful for debugging JavaScript code.

A full page is dedicated to just this tab, so we won't be going into any further detail here.

## The Performance Tab

The Performance tab allows you to analyze the runtime performance of your website. You can record and inspect various performance metrics. For the most part you won't need to use this tab, but the basic metrics it provides at the top of the page can be useful for analyzing your page performance.

This tab can also be used to throttle your CPU speed and network speed to see how your page performs under different conditions.

## Quick DevTools Tips

1. Element Picker

   - Click the element selector tool (arrow icon) (Top right corner)
   - Hover over page elements to highlight them
   - Click to inspect any element

2. Device Simulation

   - Click the device toggle icon (Computer/Phone icon) (Top right corner)
   - Test responsive designs
   - Simulate different screen sizes and devices

3. Docking

   - Change DevTools docking position (left, right, bottom, undocked)
   - Click the three vertical dots in the top right corner
   - Choose your preferred docking position

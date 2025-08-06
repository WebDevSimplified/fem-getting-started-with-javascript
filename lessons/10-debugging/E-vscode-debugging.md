---
description: Learn how to debug JavaScript directly in VSCode using the integrated debugger, launch configurations, and debugging features.
---

# Debugging in VSCode

While browser DevTools are excellent for debugging web applications, VSCode provides a powerful integrated debugging experience that lets you debug JavaScript directly in your editor.

## Why Debug in VSCode?

The main reason to use VSCode for debugging is its seamless integration with the development environment. You can set breakpoints, inspect variables, and control execution flow all within the same interface where you write your code.

The core debugging concepts (breakpoints, stepping, variable inspection) are the same as covered in the Sources Tab lesson, but VSCode provides a more streamlined experience for certain types of development.

## Setting Up JavaScript Debugging

By default, VSCode supports debugging Node.js and browser applications. Here's how to get started:

1. Open the "Run and Debug" sidebar (Ctrl+Shift+D).
2. Click "Create a launch.json file".
3. Select "Node.js" or "Web App (Chrome)" depending on your application type.
4. VSCode generates a `launch.json` file in the `.vscode` folder with default configurations.
5. Modify the `launch.json` as needed for your project.
   - Changing the URL port for web apps is usually all you need to do.

```json
// Default launch.json for "Web App (Chrome)"
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "chrome",
      "request": "launch",
      "name": "Launch Chrome against localhost",
      "url": "http://localhost:8080", // Change this to your app's URL
      "webRoot": "${workspaceFolder}"
    }
  ]
}
```

### Launching the Debugger

Once you have your `launch.json` set up all you need to do is click the green play button in the debug sidebar or press F5. This will start the debugging session and launch your application in the browser or Node.js environment.

## Creating Breakpoints

You can set breakpoints in VSCode by clicking in the gutter next to the line numbers in your code editor. A red dot indicates an active breakpoint. You can also create conditional breakpoints by right-clicking the gutter and selecting "Add Conditional Breakpoint".

## VSCode Debugging Interface

For the most part the debugging interface in VSCode is similar to the browser DevTools:

### Debug Sidebar

The Debug sidebar (Ctrl+Shift+D) shows:

- **Variables**: Local, global, and closure variables
- **Watch**: Custom expressions you want to monitor
- **Call Stack**: Function call hierarchy
- **Breakpoints**: All active breakpoints
- **Event Listener Breakpoints**: All event listeners that can pause execution

### Debug Controls

The debug toolbar appears when debugging (usually at the top center of the editor):

- **Continue (F5)**: Resume execution
- **Step Over (F10)**: Execute current line
- **Step Into (F11)**: Enter function calls
- **Step Out (Shift+F11)**: Exit current function
- **Restart (Ctrl+Shift+F5)**: Restart debugging session
- **Stop (Shift+F5)**: End debugging session

These controls work exactly like the browser debugger covered in the Sources Tab lesson.

## When to Use VSCode vs Browser Debugging

I recommend using VSCode debugging for pretty much all your applications, but the browser DevTools can still be useful if you just need to quickly inspect something or you are trying to debug an issue in a production environment.

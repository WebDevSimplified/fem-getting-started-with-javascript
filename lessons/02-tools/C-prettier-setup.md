---
description: "Setting up Prettier for automatic code formatting and understanding its benefits."
---

# Prettier Setup

Prettier is a code formatter that automatically formats your code to make it clean and readable.

## Why Use Prettier?

Writing perfectly formatted code is time consuming so we let Prettier handle it for us.

### The Problem

Both of these code examples work exactly the same, but one is much harder to read:

<!-- prettier-ignore -->
```javascript
console.log
(
  
     "Hello World"
  )
```

```javascript
console.log("Hello World")
```

### The Solution

Setup Prettier to automatically fix formatting when you save your file.

## Benefits of Prettier

✅ **Consistent formatting** - Always looks professional  
✅ **Saves time** - No manual formatting needed  
✅ **Easy to read** - Clean, standardized code  
✅ **Focus on logic** - Not spacing and style  
✅ **Team consistency** - Everyone's code looks the same

## Installation Steps

Find and install the Prettier extension for your text editor.

### 1. Install VSCode Extension

1. Click the **Extensions** button in VSCode
2. Search for "**Prettier - Code formatter**"
3. Install the one with tens of millions of downloads

#### Alternatively:

1. Launch VSCode Quick Open (Ctrl+P)
2. Run `ext install esbenp.prettier-vscode`

### 2. Enable Format on Save

1. Open **File → Preferences → Settings**
2. Click the "**Open Settings (JSON)**" icon in top-right
3. Add this configuration:

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true
}
```

## Test It Out

1. Create messy code:

<!-- prettier-ignore -->
```javascript
console.log
(
  
     "Hello World"
  )
```

2. Save the file
3. Watch it automatically format to:

```javascript
console.log("Hello World")
```

## Optional: Configure Prettier Settings

You can modify Prettier settings in your VSCode settings file.

1. Open **Settings**
2. Search for "**Prettier**"
3. Adjust settings like "**Prettier: Semi**" to remove semicolons if desired

## Important Notes

⚠️ **Prettier only works on error-free code**

- If you have syntax errors, Prettier won't format
- Fix errors first, then save to format

✅ **Works automatically**

- Just save your file
- Prettier handles all the formatting
- Focus on writing logic, not spacing

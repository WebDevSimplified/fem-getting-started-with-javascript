---
description: Learn about JavaScript's fundamental primitive data types (number, string, boolean) and the basic operations you can perform with them.
---

# Primitive Types and Operations

JavaScript has several **primitive types** - these are the basic building blocks for all data in your programs.

## Three Essential Primitives

### Number

Numbers represent any numeric value - whole numbers, decimals, negative numbers, and special numeric values.

<!-- prettier-ignore -->
```javascript
-10
25
19.99
0
Infinity
```

### String

Strings represent text data - any sequence of characters enclosed in quotes.

<!-- prettier-ignore -->
```javascript
'Sarah'
"Hello, world!"
''
""
```

- Can be created with single or double quotes
- Can be empty (just quotes with nothing inside)

### Boolean

Booleans represent true/false values.

```javascript
true
false
```

## Basic Operations on Primitives

Operations are actions you can perform with primitive values. Each type supports different operations.

### Number Operations

- Arithmetic Operations
  <!-- prettier-ignore -->
    ```javascript
    // Basic math
    10 + 3 // 13
    10 - 3 // 7
    10 * 3 // 30
    10 / 3 // 3.333...

    // Order of operations applies
    2 + 3 * 4 // 14 (not 20)
    (2 + 3) * 4 // 20
    ```

- Comparison Operations

  ```javascript
  85 == 92 // false
  85 != 92 // true

  85 < 92 // true
  85 > 92 // false
  85 <= 85 // true
  92 >= 90 // true
  ```

### String Operations

- Concatenation (Joining Strings)

  ```javascript
  "Kyle" + " " + "Cook" // "Kyle Cook"
  ```

- String Comparison

  ```javascript
  "apple" == "apple" // true
  "apple" != "apple" // true

  // Alphabetical comparison
  "apple" < "banana" // true ("apple" comes before "banana")
  ```

### Boolean Operations

- Logical Operations

  ```javascript
  true && false // false (AND)
  true || false // true (OR)
  !true // false (NOT)
  ```

- Boolean Comparison

  ```javascript
  true == true // true
  true == false // false
  true != false // true
  ```

## Determining Types

You can check the type of any value using the `typeof` operator:

```javascript
typeof 42 // "number"
typeof "Hello" // "string"
typeof true // "boolean"

typeof 1 == typeof 2 // true
```

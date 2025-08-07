---
description: Learn how the this and new keywords work in JavaScript, including their uses in classes, objects, and different contexts.
---

# The `this`/`new` Keywords

The `this`/`new` keywords are two of the most confusing concepts in JavaScript, but they're also incredibly powerful. Understanding `this`/`new` is essential for working with objects, classes, and many built-in JavaScript features.

⚠️ **WARNING:** This is a tricky topic, so take your time to understand it fully!

## What is `this`?

The `this` keyword refers to an object - but **which** object depends on how and where `this` is used. Think of `this` as a special variable that JavaScript automatically creates, and its value is determined by the context in which it is used.

```javascript
console.log(this) // In the browser, this by default refers to the window object
```

### `this` With Objects

When `this` is used inside an object method, it refers to the object itself:

```javascript
const person = {
  name: "Alice",
  age: 25,
  greet() {
    console.log(`Hello, my name is ${this.name}`)
  },
}

person.greet() // "Hello, my name is Alice"
```

This is useful for accessing properties of the object from within its methods.

## Classes

Classes provide an alternate way to define objects and their methods. Inside class methods, `this` refers to the instance of the class. To create a class in JavaScript, you use the `class` keyword followed by the class name (start with a capital letter) and finally put all the class methods and properties inside curly braces `{}`.

```javascript
class Person {
  constructor(name, age) {
    this.name = name
    this.age = age
  }

  greet() {
    console.log(`Hello, my name is ${this.name}`)
  }
}

const alice = new Person("Alice", 25)
alice.greet() // "Hello, my name is Alice"
```

Classes are a way to create templates for objects and encapsulate related data and behavior together.

### Class Components

Let's break down the key components of this code:

#### Constructor

The `constructor` method is a special method that runs when you create a new instance of the class.

```javascript
class Person {
  constructor(name, age) {
    this.name = name
    this.age = age
  }
}
```

The best way to think of the constructor is that it is a function that:

1. **Creates a new empty object**: `this = {}` (automatic)
2. **Runs your constructor code**: Your code sets properties on `this`
3. **Returns the object**: `return this` (automatic)

#### Defining Methods

You can define methods inside the class using the same syntax as object methods:

```javascript
class Person {
  greet() {
    console.log(`Hello, my name is ${this.name}`)
  }
}
```

The syntax is essentially the same as defining a function but you just leave off the `function` keyword. The method will automatically have access to `this`, which refers to the instance of the class.

#### Creating Instances

To create an instance of a class, you use the `new` keyword followed by the class name and parentheses:

```javascript
const alice = new Person("Alice", 25)
```

This runs our constructor and returns a new object with the properties and methods defined in the class.

### Classes In Depth

There are many advanced features you can use with classes, but they are not nearly as important as understanding what classes are and how `this`/`new` work together.

Personally, I don't use classes much in my own code, but depending on your coding style you may use them more often.

## Built-in Examples

JavaScript has many built-in examples of using `new` to instantiate objects. For example, the `Date` object is created using `new Date()`:

```javascript
// Creating a Date object
const now = new Date()
console.log(now) // Current date and time

// Date uses `this` internally
console.log(now.getMonth())
console.log(now.getDay())
console.log(now.getDate())
```

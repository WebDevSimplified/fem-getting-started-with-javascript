---
description: Learn how to create and work with objects to organize related data and functions together.
---

# Objects

Objects are the most important variable type in JavaScript because they allow you to organize your data.

## What is an Object?

An object is a collection of related information stored together in key-value pairs. Think of it like a box that holds different pieces of information about something.

```javascript
// Separate variables (not organized)
const name = "Kyle"
const age = 25
const favoriteNumber = 3

// Object (organized together)
const person = {
  name: "Kyle",
  age: 25,
  favoriteNumber: 3,
}
```

## Creating Objects

Use curly braces `{}` to create objects, with key-value pairs separated by commas.

```javascript
const person = {
  name: "Kyle",
  age: 25,
  favoriteNumber: 3,
}
```

### Key-Value Pairs

Each piece of data in an object consists of:

- **Key**: The name of the property
- **Value**: The data stored in that property

Keys use the same naming conventions as variables (camelCase, no spaces) and the values can be any data type, including other objects or functions. The key and value are separated by a colon `:`.

```javascript
const person = {
  name: "Kyle", // key: "name", value: "Kyle"
  age: 25, // key: "age", value: 25
  favoriteNumber: 3, // key: "favoriteNumber", value: 3
}
```

## Accessing Object Properties

Use dot notation to access properties:

```javascript
const person = {
  name: "Kyle",
  age: 25,
  favoriteNumber: 3,
}

console.log(person.name) // "Kyle"
console.log(person.age) // 25
console.log(person.favoriteNumber) // 3
```

## Adding Functions to Objects

Objects can contain functions (often called **methods** when inside objects):

```javascript
const person = {
  name: "Kyle",
  age: 25,
  favoriteNumber: 3,
  sayHi: function () {
    console.log("Hi")
  },
}

person.sayHi() // "Hi"
```

### Shorthand Function Syntax

You can write functions in objects without the `function` keyword:

```javascript
const person = {
  name: "Kyle",
  age: 25,
  favoriteNumber: 3,
  sayHi() {
    console.log("Hi")
  },
  sayGoodbye() {
    console.log("Goodbye")
  },
}

person.sayHi() // "Hi"
person.sayGoodbye() // "Goodbye"
```

## Real-World Example: `console.log`

You've been using objects all along! `console` is an object with a `log` function:

```javascript
console.log("Hello") // console is an object, log is a method

// This is similar to:
const console = {
  log(message) {
    // Display the message
  },
}
```

## Bracket Notation (Alternative Access)

You can also access properties using brackets with strings:

```javascript
const car = {
  make: "Nissan",
  model: "370Z",
}

console.log(car["make"]) // "Nissan"
console.log(car.make) // "Nissan" (preferred)
```

The only time you need to use bracket notation is when the property name is stored in a variable:

```javascript
const property = "make"
console.log(car[property]) // "Nissan"
```

## Nested Objects

Objects can contain other objects or arrays:

```javascript
const person = {
  name: "Kyle",
  address: {
    street: "12345 Main Street",
    city: "Somewhere",
  },
  hobbies: ["weightlifting", "programming"],
}

console.log(person.name) // "Kyle"
console.log(person.address.street) // "12345 Main Street"
console.log(person.address.city) // "Somewhere"
console.log(person.hobbies[0]) // "weightlifting"
```

## Practice Exercise

Create an object called `book` with the following properties:

1. `title` - the book title
2. `author` - an object with `firstName` and `lastName`
3. `yearPublished` - the year the book was published
4. `publish` - A function that prints the message `"Publishing your book"`

<details>
<summary>Solution</summary>

```javascript
const book = {
  title: "The Way of Kings",
  author: {
    firstName: "Brandon",
    lastName: "Sanderson",
  },
  yearPublished: 2010,
  publish() {
    console.log("Publishing your book")
  },
}
```

</details>

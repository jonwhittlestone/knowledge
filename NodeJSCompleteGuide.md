# NodeJS - The Complete Guide

My notes on Max's course

- python vs. javscript syntax comparison: https://goo.gl/fS9Hhw

---

## Module 02. Optional JavaScript - a quick refresher

- 12 concepts that will level up your js skills https://goo.gl/iEeDqC

### 02-009 Module Intro
### 02-010 JavaScript in a nutshell
### 02-011 The Core Syntax

### 02-012 let const
- use `let` instead of `var` because we have..
- `const` to assign a variable that never changes to be clear about our intentions


### 02-013 Understanding arrow functions
- `const summarizeUser = (p1, p2) => {//definition in function body};`
- use `this`
- can be simplified even more if there is just one return statement 

### 02-014 Objects
- how to write a function in an object
 
### 02-015 Arrays/arrays methods
- `map()` allows you to transform an array  and returns a new array `newArray = existingArray.map(hobby => { return 'Hobby: ' + hobby })`
- or just
- `newArray = existingArray(hobby=> 'Hobby' + hobby)`


### 02-016 array objects reference types
- reference types only store a pointer to an address in memory and so a `const` can be added to 
- not really editing the `const` thing, just the thing it's ponting at


### 02-017 spread/rest operators
- to avoid errors where we copy/duplicate the array and add the new thing, 
- `hobbies.slice()` just copies the array and can narrow down the range of things you wish to copy
- instead of `slice()`, spread operator, `const copiedArray = [...hobbies]; `
- ^ this unwraps everything in hobbies into the new array
- rest operator is called when used to merge multiple elements into an array (like in a function definition)


### 02-018 destructuring
- object destructuring
- add curly braces in the argument list, so the property will pulled out of the object
- as seen in vue store
- syntax for understandable code where we are clear about the incoming object and its use
- `const printName = ({name}) => {console.log(name); }`
- or can just use in an array
- `const {name, age } = hobbies;`

### 02-019 Async code, promises
- setTimeout example is async code since it doesn't finish immediately
- the only limitation with synchronous code is your hardware
- js doesn't block code execution 
- manual promise creation (most packages do this for you)
- if the function returns a promise object, when calling the function, you can then chain `then()` statements and makes it more readable than callbacks
- another way to manage this is async/await

---

## Module 03. Understanding the basics

### 03-023 Module Intro

---

## Module 04. Improved dev workflow and debugging

### 04-040 Intro

---

## Module 05. Working Express.js

### 05-056 Intro

---

## Module 06. Working with Dynamic Content Adding templating options

### 06-076 Module Intro

---

## Module 07. The Model View Controller

### 07-093 Intro

---

## Module 08. Optionally Enhancing the App

### 08-102 Intro

---

## Module 09. Dynamic Routes Advanced Modules

### 09-111 Intro

---

## Module 10. SQL Introduction

### 10-131 Intro

---

## Module 11. Understanding Sequelize

### 11-145 Intro

---

## Module 12. Working with NoSQL using MongoDB

### 12-172 Intro

---

## Module 13. Working with Mongoose

### 13-205 Module Introduction

---

## Module 14. Sessions Cookies

### 14-226 Intro

---

## Module 15. Adding Authentication

### 15-246 Intro

---

## Module 16. Sending Emails

### 16-266 Intro

---

## Module 17. Advanced Authentication

### 17-272 Intro

---

## Module 18. Understanding validation

### 18-284 - Intro

---

## Module 19. Error Handling

### 19-301 Intro

---

## Module 20. File Upload Download

### 20-314 Intro

---

## Module 21. Adding Pagination

### 21-333 Intro

---

## Module 22. Understanding Async Requests

### 22-342 Intro

---

## Module 23. Adding Payments

### 23-349 Intro

---

## Module 24. Working with REST APIs - The Basics

### 24-354 Intro

---

## Module 25. Working with REST APIs - The Practical Application

### 25-365 Intro

---

## Module 26. Understanding Async Await in Node.js

### 26-394 Intro

---

## Module 27. Understanding Websockets Socket.io

### 27-400 Intro

---

## Module 28. Working GraphQL

### 28-414 Intro

---

## Module 29. Deploying our App

### 29-442 Intro

---

## Module 30. Node.js as a Build Tool using NPM

### 30-458 Intro

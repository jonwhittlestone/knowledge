# NodeJS - The Complete Guide

My notes on Max's course

- python vs. javscript syntax comparison: https://goo.gl/fS9Hhw
- A lot of the Express' typical web framework patterns are the same as for Laravel and Django

---

## M02. Optional JavaScript - a quick refresher

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

- `map()` allows you to transform an array and returns a new array `newArray = existingArray.map(hobby => { return 'Hobby: ' + hobby })`
- or just
- `newArray = existingArray(hobby=> 'Hobby' + hobby)`

### 02-016 array objects reference types

- reference types only store a pointer to an address in memory and so a `const` can be added to
- not really editing the `const` thing, just the thing it's ponting at

### 02-017 spread/rest operators

- to avoid errors where we copy/duplicate the array and add the new thing,
- `hobbies.slice()` just copies the array and can narrow down the range of things you wish to copy
- instead of `slice()`, spread operator, `const copiedArray = [...hobbies];`
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

## M03. Understanding the basics

### 03-023 Module Intro

### 03-024 How the Web works

### 03-025 Creating a node server

- create in `app.js`
- core modules: http(s)/fs/path/os
- explanation of event-driven architechture where you pass function or anonymous function to `http.createServer()` where we define the `RequestListener`
- can also use an arrow function eg

```
  const server = http.createServer((req,res) => {

  });
```

### 03-026 Node.js program lifecycle

- the event loop which keeps on runing as long as there are event listeners registered
- ie. we didn't unreigster from the incoming request listener, and `RequestListener` is ongoing
- the entire node process uses one thread
- unregister with `process.exit()` hard exited our event loop

### 03-028 Understanding requests

### 03-029 Sending responses

- using `res.write('<html>')`
- easier with expressjs

### 03-031 Routing requests

- using a conditional on `res.url`
- must `return res.end()` so we exit out of anonymou function and unregister from request listener

### 03-032 Redirecting requests

- uses `fs` module for a given url route and writes to the filesystem and then redirects with `res.setHeader('Location','/')`

### 03-033 Parsing request bodies

- streams & buffers explanation
- request is read in chunks until fully parsed - the benefit of this is when data is incoming, the entire file doesn't have to be parsed before we can start doing things with it
- A buffer organises these chunks (analagous to bus stops) to hold multiple chunks

- we create an event listener on our own, we listen for `data` event which fires when a new chunk is ready to be read

```
  if (url === '/message' && method === 'POST') {
    const body = [];
    req.on('data', (chunk) => {
      console.log(chunk);
      body.push(chunk);
    });
    req.on('end', () => {
      const parsedBody = Buffer.concat(body).toString();
      const message = parsedBody.split('=')[1];
      fs.writeFileSync('message.txt', message);
    });
    res.statusCode = 302;
    res.setHeader('Location', '/');
    return res.end();
  }
```

### 03-034 Understanding Event Driven Code Execution

- order of execution is not necessarily the order in which you write it
- nodejs uses a pattern where you pass in a function to a function and node will execute the passed-in functions at a later point in time (asynchronously)
- can register code (in node's internal registry) to be run at some point in the future, but not necessarily right now
- this means node doesn't need to pause and is free to handle other incoming requests

### 03-035 Blocking and Non-Blocking code

- `writeFileSync()` is the synchronous code where we block execution until the file is written
- better to use `writeFile()` where you can specify a callback as third argument for code to execute when it's done
- refactored to:

```
  if (url === '/message' && method === 'POST') {
    const body = [];
    req.on('data', chunk => {
      console.log(chunk);
      body.push(chunk);
    });
    return req.on('end', () => {
      const parsedBody = Buffer.concat(body).toString();
      const message = parsedBody.split('=')[1];
      fs.writeFile('message.txt', message, err => {
        res.statusCode = 302;
        res.setHeader('Location', '/');
        return res.end();
      });
    });
  }
```

- nodejs is high performance as it never blocks main code execution, never blocks server, just tells the operating system 'do this, do that'

### 03-036 Looking behind the scenes

- Single Thread, Event Loop & Blocking Code
- The event loop that handles all the callback and is started by nodejs
  - checks if any timers running like `setTimeout` and `setInterval`
  - are there any pending callbacks
  - poll phase where nodejs looks for new I/O events
  - close event callbacks
- we may end event look with `process.exit`
- `refs` is the count of open callbacks

### 03-037 Using the node modules system

- how to connect multiple files

- exporting in nodejs with `module.exports = requestHandler;` at the end of the file
- split our code over two files
- or `module.exports.handler = requestHandler` so there is only one `module.exports`
- new nodejs syntax `exports.handler = requestHandler`

### 03-038 Summary

- Program Lifecycle: non-blocking JS code and uses event-driven code for running logic
- loop keeps waiting for new events and dispatches some action to the OS
- Async code: register some code to be executed in the future instead of blocking the main thread.
- Parse request data in chunks

---

## M04. Improved dev workflow and debugging

### 04-040 Intro

### 04-041 Understanding NPM scripts

- can use an npm file like a `MAKE` file to do `npm run {script name}`

### 04-042 Installing 3rd Party Packages

- auto-restart mechanism with `npm install nodemon --save-dev`

### 04-044 Using nodemo for autorestarts

### 04-046 Types of Errors

### 04-047 - Finding fixing syntax errors

### 04-048 - Dealing with runtime errors

- when we don't `return` from callbacks
- scroll to top of error message and read it
- Look at the code before the offending line number

### 04-049 - Dealing with logical errors

- node.js debugger with vscode integration

### 04-050 - Using the debugger

### 04-051 - Restarting the debugger

- to restart the debugger if we change our code, add a configuration in `launch.json`
- `"restart": true`
- `"runtimeExecutable": "nodemon"`
- add nodemon globally

### 04-053 - changing variables in the debug console

---

## M05. Working with Express.js

### 05-056 Intro

### 05-057 What is Express

### 05-058 Installing express

- `app` is a valid request handler

```
const app = express();

const server = http.createServer(app);
```

### 05-059 adding middleware

- the incoming request is automatically funelled through multiple functions until you send a response
- this pluggable nature of express means you can easily add 3rd party packages

- after creating the app object, call a method `use` which allows us to add a new middleware function

```
  //
  app.use((req, res, next)) => {

      // must be included so the
      // next middleware can be applied
      // otherwise, it will die and not progress
      next();

  });
```

- use `next()` to progress program flow to the next middleware function, or send a response

### 05-060 How middleware works

- send a response with an express utility function `res.send()`

### 05-061 Expressjs looking behind the scenes

- github

### 05-062 Handling different routes

- filter for different requests to different urls
- docs: https://expressjs.com/en/4x/api.html#app.use

- can order the below depending on what routes we wish to catch with filter (order of precendence) to funnel requests to the desired place

```
app.use('/add-product',(req, res, next) => {
  res.send('<h1>Add Product Page</h1>');
});
```

### 05-063 Parsing incoming requests to ext

- convinience function for redirect
- `npm install --save body-parser`
- `app.user(bodyParser.urlencoded(extended:false))`
- this is simpler than our custom approach we used before

### 05-064 Limiting middleware to POST requests

- another form of filtering

```
app.post('/product',(req, res, next) => {
  console.log(req.body);
});
```

### 05-065 Using express router

- often-used convention is to put routing related code in a `/routes` folder
- `const router = express.Router();`
- can then use

```
router.get('/add-product', (req, res, next) => {
  console.log('do stuff with this valid middleware function');
});
module.exports = router;
```

### 05-066 Adding a 404 error page

- if nodejs doesn't find a middleware to execute, we make it to the botttom and the request must be handled by a catch all filter

```
app.use((req,res, next) => {
  res.status(404).send('<h1>page not found</h1>');
});
```

### 05-067 filtering paths

- a common starting segment of the url (eg. `/admin/') can be added to the`use` so it doesn't have to be repeated and in the oursourced js route file, it is then implict

### 05-068 creating HTML pages

- change to rendering from `/views` folder

### 05-069 Serving HTML pages

- `res.sendFile()`

```
  res.sendFile(
    path.join(__dirname, '../', 'views', 'shop.html)
  );
```

### 05-070 returing a 404 page

### 05-071 Using a helper function for navigation

- create a helper in `/util` to get the `rootDir` to get path to the root file
- use global `process` variable that is available in all files

### 05-072 styling

- flexbox for stying `<li>` next to each other

### 05-073 serving files statically

- use external css files in `/css` directly forwarded to the filesystem
- similar to registering static middleware `app.use(express.static('/public'));`

### 05-074 wrap up

- Express.js is a Node.js framework - a package that adds a bunch of utility functions and tools an a slear set of rules on how the app should be built ('middleware')

---

## M06. Adding Dynamic Content & Templating options

### 06-076 Module Intro

### 06-077 sharing data across requests

- this method is data that exists on the node server and is shared across all requests, typically won't want this but good for demonstrating

### 06-078 Templating Engines

- EJS / Pug / Handlebars

### 06-079 Installing Pug

### 06-080 Outputting Dynamic content

- bind the products to the prods key in the render method

```
  res.render('shop', {
    prods: products,
    pageTitle: 'Shop',
    path: '/',
    hasProducts: products.length > 0,
    activeShop: true,
    productCSS: true
  });
```

- use pug to output single values, conditionally output with if/else, or loop through

### 06-081 - Converting HTML files to pug templates

### 06-082 - Adding a layout

- using `block content`

### 06-083 - Adding a layout

### 06-084 - Finishing pug layout

- setting `active` class

### 06-085 - working with handlebars

- `.hbs` extension

### 06-086 - Converting project to handlebars

### 06-087 - Adding layout file to hbs

### 06-088 - working with EJS

- syntax: `<%= pageTitle %>`
- can use javascript in the template

### 06-089 - working on the layout with partials

- shared includes in `includes/` sub directory

### 06-090 - wrap up

- Must specify/register render engine

---

## M07. MVC

### 07-092 Intro

### 07-093 What is MVC

- in an Express App, controllers can be split up accross middleware

### 07-094 - Adding Controllers

- in `controllers/products.js` folder:

```
exports.getAddProduct = (req, res, next) => {
  res.render('add-product', {
    pageTitle: 'Add Product',
    path: '/admin/add-product',
    formsCSS: true,
    productCSS: true,
    activeAddProduct: true
  });
};
```

- In respective route file: `require` the controller

```
const productsController = require('../controllers/products');
```

### 07-095 - Finishing the controllers

- creating an error controller `get404`
- use it from `app.js` with `app.use(errorController.get404)`

### 07-096 - Adding a Product Model

- Represents a single product entity in `models/product.js` by storing in an ES6 class

```

module.exports = class Product {
  constructor(t) {
    this.title = t;
  }

  save() {
    getProductsFromFile(products => {
      products.push(this);
      fs.writeFile(p, JSON.stringify(products), err => {
        console.log(err);
      });
    });
  }

  static fetchAll(cb) {
    getProductsFromFile(cb);
  }
};
```

- `require` it from the controller and then instantiate in the relevant controller action

```
const Product = require('../models/product');
```

### 07-097 - Store data in files via model

- create a basic `save()` method in the model in which

  1. a data file containing json is read into memory
  2. the json is parsed into memory
  3. the data is pushed onto that products array
  4. data is saved back into the file via the `stringify` method

- code for above:

```
// models/product.js
...

  save() {
    const p = path.join(
      path.dirname(process.mainModule.filename),
      'data',
      'products.json'
    );

    // step 1
    fs.readFile(p, (err, fileContent) => {
      let products = [];
      if (!err) {
        // step 2
        products = JSON.parse(fileContent);
      }
      // step 3
      products.push(this);
      // step 4
      fs.writeFile(p, JSON.stringify(produts));
      });
  }
```

- to ensure `this` refers to the product (the class), an arrow function should be used or `this` will lose itso context and not refer to the class anymore

- `static fetchAll() {}` is modified so that it reads from the file system

### 07-098 - Fetching data from files via the model

- The problem with having async code for `readFile()` in `fetchAll()` is that data won't be returned because it is just registers the callback in its event emitter registry
- the way around this is to accept a callback for `fetchAll` where the callback function is executed once it is done

```
  static fetchAll(cb) {
    fs.readFile(p, (err, fileContent) => {
      let products = [];
      if (err) {
        return cb([]);
      }
      cb(JSON.parse(fileContent));
      });
  }
```

- Where it is being called, in the controller, pass in a callback function to say that when I eventually get my products, do more stuff

```
// controllers/products.js

  Product.fetchAll(products => {
    res.render('shop', {
      prods: products,
      pageTitle: 'Shop',
      path: '/',
      hasProducts: products.length > 0,
      activeShop: true,
      productCSS: true
    });
```

- ie. `fetchAll` takes a function it should execute once it's done

### 07-099 - Refactoring the file storage code

- Define an empty function

```
  const getProductsFromFile = () => {

  }
```

- create an anonymous function in `save()` where I know we will get the products

```
save() {
  getProductsFromFile(products => {
    // then put in code where we append a new product and save to filesystem
    products.push(this);
    fs.writeFile(p, JSON.stringify(products), err => {
      console.log(err);
    });
  });
}

```

### 07-0100 - Wrap up on mvc

---

## M08 Enhancing the App

### 08-102 Intro

- Adding just more views/controllers so mainly copy/pasting code

### 08-103 Creating the shop structure

### 08-104 Navigation

### 08-105 Registering routes

### 08-106 Storing product data

- adding more properties to `Product` class

### 08-107 Displaying product data

### 08-108 Editing / Deleting products links

### 08-109 Adding another item

---

## M09. Dynamic Routes Advanced Modules

### 09-111 Intro

- passing route and query params

### 09-112 Prep

### 09-114 Adding product ID to the path

- from view ..

### 09-115 Extracting ID

- extract with `const prodId = req.body.productId`

### 09-116 Loading Product detail data

- add model method `findById(id,cb)`
- the callback will be executed once we're done finding the product
- in `getProductsForFile` before we return products, filter out the one product whose id matches the argument id
  (using javascript `find()` method)

### 09-117 Rendering the product detail data

### 09-118 Passing data with POST requests

- route accepts POST request with `router.post('/cart', shopController.postCart);`
- `add-to-cart.ejs` is an include that can be included in other partials

### 09-119 Adding a cart model

- start with

```
  module.exports = class Cart {
    // allows to instantiate
    constructor() {}
  }
```

- and add logic for class method `static addProduct()`
- use javscript spread operator to create new object from `existingProduct` into `updatedProduct` (and then the quantity is set to the old quanitity plus one)
- in controller action, use utility class method `Cart.addProduct(prodId, product.price)`

### 09-120 Query Parameters (for editing)

- get from query string with `const prodId = req.params.productId;`
- use `editing` template variable so can populate form data with product data

### 09-121 Pre-populating the page with data

### 09-122 Linking to the edit page

### 09-123 Editing the product data

- conditionally include the `product.id` as a hidden input variable

### 09-124 Adding the Product Delete functionality

### 09-125 Deleting cart items

- `static deleteProduct(id, productPrice) {}` in `cart.js`

### 09-126 Displaying cart items on the cart page

- working with a lot of depending async actions can be simplified rather than multiple callbacks
- ie. see controller action:

```

exports.getCart = (req, res, next) => {
  Cart.getCart(cart => {
    Product.fetchAll(products => {
      const cartProducts = [];
      for (product of products) {
        const cartProductData = cart.products.find(
          prod => prod.id === product.id
        );
        if (cartProductData) {
          cartProducts.push({ productData: product, qty: cartProductData.qty });
        }
      }
      res.render('shop/cart', {
        path: '/cart',
        pageTitle: 'Your Cart',
        products: cartProducts
      });
    });
  });
};
```

### 09-127 Delete from cart

### 09-128 Fixing a delete product bug

### 09-129 Wrap up

---

## M10. SQL

### 10-131 Intro

---

## M11. Understanding Sequelize

### 11-145 Intro

---

## M12. NoSQL using MongoDB

### 12-172 Intro

---

## M13. Mongoose ODM

### 13-205 Module Introduction

---

## M14 Sessions

### 14-226 Intro

---

## M15. Adding Authentication

### 15-246 Intro

---

## M16. Sending Emails

### 16-266 Intro

---

## M17. Advanced Authentication

### 17-272 Intro

---

## M18. Validation

### 18-284 - Intro

---

## M19. Error Handling

### 19-301 Intro

---

## M20. File Upload Download

### 20-314 Intro

---

## M21. Adding Pagination

### 21-333 Intro

---

## M22. Understanding Async Requests

### 22-342 Intro

---

## M23. Adding Payments

### 23-349 Intro

---

## M24. Working with REST APIs - The Basics

### 24-354 Intro

---

## M25. Working with REST APIs - The Practical Application

### 25-365 Intro

---

## M26. Understanding Async Await in Node.js

### 26-394 Intro

---

## M27. Websockets Socket.io

### 27-400 Intro

---

## M28. GraphQL

### 28-414 Intro

---

## M29. Deploying our App

### 29-442 Intro

---

## M30. Node.js as a Build Tool using NPM

### 30-458 Intro

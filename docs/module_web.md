# Web Module Questions

## Functional patterns

<br>

###  What is a callback function?

A callback function is a function that is passed into another piece of code as an argument. The code is expected to invoke the callback function as part of its routine. A callback function can both be a named or an anonymous function.

<br>

###  What is ECMA script ? What is the difference between Javascript & ECMA script ?

- ECMAScript (European Computer Manufacturers Association Script) is a scripting language specification. It is a scripting language standard intended to ensure the interoperability of web pages across different browsers.
- JavaScript is a high level programming language that implements the ECMAScript standard / specification, and it is one of the core technologies of the world wide web.

<br>

###  What is the difference between `let` & `var` ?

Both of the keywords are used to define variables, but they differ in some aspects.
One aspect is the **scope of the variable**.
A variable declared with the **var** keyword is scoped to the immediate function body, while one declared with **let** is scoped to the enclosing block denoted by { }.
Example:
```JS
function run() {
  var foo = "Foo";
  let bar = "Bar";

  console.log(foo, bar); // Foo Bar

  {
    var moo = "Mooo"
    let baz = "Bazz";
    console.log(moo, baz); // Mooo Bazz
  }

  console.log(moo); // Mooo -> it is scoped to the entire function
  console.log(baz); // ReferenceError -> it was only scoped to the previous code block enclosed in { }
}

run();
```

An other aspect is **hoisting**:
`var` variables are initialized at the start of the code with "undefined" value. <br>
`let` variables are not initialized until declared, and we get a ReferenceError when calling them. <br>

Yet an other aspect they differ in is the **global object property**:
`var` variables are creating a property in the global object. <br>
`let` variables are not available in the global object. <br>
Example:

```JS
var foo = "Foo";  // globally scoped
let bar = "Bar"; // not allowed to be globally scoped
console.log(window.foo); // Foo
console.log(window.bar); // undefined
```

And lastly `var` variable may be redeclared, while `let` variables may be not.

```JS
'use strict';
var foo = "foo1";
var foo = "foo2"; // No problem, 'foo1' is replaced with 'foo2'.

let bar = "bar1"; 
let bar = "bar2"; // SyntaxError: Identifier 'bar' has already been declared
```

<br>

###  Write an example where using the `var` declaration instead of the `let` could create a hard to debug code.

```JS
var age = 60;
var ages = [];
for (var i = 0; i < 5; i++) {
    var age = i * 2;
    ages.push(age);
}
console.log(ages);
console.log('my age is now:', age);
```

<br>

###  Give a practical example where you would use the `reduce` function in javascript.

```JS
const users = [
    { name: "optimius-prime", followers: 9999, difference: 12 },
    { name: "doombringer", followers: 1044, difference: 99 },
    { name: "barbie", followers: 11012, difference: 1099 },
    { name: "ken", followers: 8239, difference: -144 }
]

const totalNumberOfFollowers = users.reduce((acc, curr) => acc += curr.followers, 0);
```

<br>

###  Give a practical example where you would use the `map` function in javascript.

```JS
const users = [
    { name: "optimius-prime", followers: 9999, difference: 12 },
    { name: "doombringer", followers: 1044, difference: 99 },
    { name: "barbie", followers: 11012, difference: 1099 },
    { name: "ken", followers: 8239, difference: -144 }
]
//different object with percentage extra (array of objects, spread op doesn't work because objects are copied with reference...)
const usersWithChangePercent = JSON.parse(JSON.stringify(users)).map(user => {
  user.change = (user.difference/user.followers * 100).toFixed(2) + '%';
  return user;
});
```

<br>

###  Give a practical example where you would use the `filter` function in javascript.

```JS
const users = [
    { name: "optimius-prime", followers: 9999, difference: 12 },
    { name: "doombringer", followers: 1044, difference: 99 },
    { name: "barbie", followers: 11012, difference: 1099 },
    { name: "ken", followers: 8239, difference: -144 }
]

const over9000 = users.filter(user => user.followers > 9000);
```

<br>

### Web basics

<br>

###  What is a web server?

A web server is a software and a hardware that uses HTTP (HyperText Transfer Protocol) and other protocols to respond to client requests made over the World Wide Web. The main job of a web server is to display website content through storing, processing and delivering webpages to users.
Web server hardware is connected to the internet and allows data to be exchanged with other connected devices, while web server software controls how a user accesses hosted files.

<br>

###  Explain the client-server architecture.

- A server is the one who provides requested services.
- Clients are the ones who request services.

Client server architecture is a computing model in which the server hosts, delivers, and manages most of the resources and services requested by the client. It is also known as the networking computing model or client server network as all requests and services are delivered over a network. The client-server architecture has other systems connected over a network where resources are shared among the different computers.

The process:
- The user enters the uniform resource locator (URL) of the website or file and the browser sends a request to the domain name system (DNS) server.
- The DNS server looks for the address of the web server and the DNS server responds with the IP address of the web server.
- After the DNS server responds, the  browser sends over an HTTP or HTTPS request to the web server’s IP, which was provided by the DNS server.
- The server then sends over the necessary files of the website.
- Finally, the browser renders the files and the website is displayed.

More generally:
Client-server architecture can be software communicating with each other. e.g. MongoSH (client) communicating with MongoDaemon Service / Process. Client ~ Interface communicating with a Service/Software.

<br>

###  What is the difference between synchronous and asynchronous execution?

When a code is executed **synchronously**, it means that the next line of code starts executing only after the previous line has finished.

When a code is executed **asynchronously**, it means that the next line of code will start executing after the previous line has started, regardless if it has finished or not.

<br>

###  What is `npm`? Why is it useful?

Npm, short for Node Package Manager is a package manager for the JavaScript programming language and is the world's largest Software Registry. It contains over 800.000 code packages. Open-source developers use npm to share software. It is free to use, requires no registration or logging in. Npm is the default package manager for JavaScript runtime environment Node.js.
Npm also manages version controlling of these libraries / dependencies.

<br>

###  What is the difference between the `dependencies` & `devDependencies` in a `package.json` file ?

DevDependencies are modules which are only needed throughout the development of a project, while dependencies will be needed after development as well. E.g. Nodemon is a module that automatically restarts the server when a file is changed during development. A server restart due to a file change is rather unwanted in a live environment.

<br>

###  What would be the impact of javascript `fetch` if it was not asyncronous ?

It would halt the running of the software code until all the requested or send data has been transferred.

<br>

###  What benefits would bring to a developer to use the `Postman` application ?

Postman is used to test APIs. Using Postman, one can send various requests with various content to different APIs, create tests, store test routines, results and data. It is also possible to copy working API request codes in different languages (for example JavaScript) and copy-paste it into a project. Using Postman can accelerate development, implementation of APIs into code.

In our context a backend can be tested with Postman without a line of frontend.

<br>

###  List the parts of the URL.

A URL consists of ______five______ parts:
- protocol: "https://"
- subdomain: "blog."
- (second-level) domain name: "hubspot"
- top-level domain: ".com"
- port: ":80"
- path: "/marketing/"
- query: "?"
- parameters: "docid=1141213&hl=en"
- fragment: "#00h02m30s"

<br>

###  What is query parameter?

A query parameter is part of a URL (uniform resource locator) that assigns values to specified parameters. A query string commonly includes fields added to a base URL by a Web browser or other client application, for example as part of an HTML, choosing the appearance of a page, or jumping to positions in multimedia content.

https://www.google.com/search?q=how+to+successfully+pass+the+pa

<br>

###  What kind of HTTP status codes do you know?

**- 1xx informational response – the request was received, continuing process**

- 100: Continue

**- 2xx successful – the request was successfully received, understood, and accepted**

- **200: OK**
- 201: Created
- 202: Accepted

**- 3xx redirection – further action needs to be taken in order to complete the request**

- 301: Moved Permanently
- 302: Found (~ Moved temporarily)
- **304: Not modified**
- 305: Use Proxy
- 307: Temporary redirect
- 308: Permanent redirect

**- 4xx client error – the request contains bad syntax or cannot be fulfilled**

- **400: Bad request**
- 401: Unauthorized
- 402: Payment required
- 403: Forbidden
- **404: Not found**
- 405: Method not allowed
- 406: Not acceptable
- 408: Request Timeout
- 418: I'm a teapot

**- 5xx server error – the server failed to fulfil an apparently valid request**

- **500: Internal server error**
- 502: Bad Gateway
- 503: Service unavailable

<br>

###  How does an HTTP Request look like? What are the most relevant HTTP header fields?

1. Start-line (eg. POST / HTTP/1.1)
- HTTP method (GET, POST, PUT, DELETE, HEAD, CONNECT, OPTIONS, TRACE, PATCH), describes the action
- request target, usually URL or absolute path of the protocol, port and domain
- HTTP version

2. HTTP headers (eg. Host: localhost:8000, Content-Type: multipart/form-data; boundary=-12656974, Content-Length: 345)
- General headers ("Via")
- Request headers ("User-Agent", "Accept", "Referer")
- Representation headers ("Content-Type", eg: "text/html", "multipart/form-data; bondary=something", "application/json" for JSON text)

3. Blank line

4. Body (*optional*)
- fetching requests (GET, HEAD? DELETE, OPTION) usually do not have one
- Two categories: 
  - Single-resource bodies, defined by two headers: Content-Type and Content-Length
  - Multiple-resource bodies, consisting of a multipart body, each containing a different bit of information, eg. HTML forms


<br>

###  How does an HTTP Response look like? What are the most relevant HTTP header fields?

1. Status line (Eg. HTTP/1.1 404 Not found)
- Protocol version
- Status code (see above)
- Status text

2. Headers
- General headers (Connection: Keep-Alive, Date: ..., Keep-Alive: timeout=5, max=999, etc)
- Response headers (Vary, Accept-Ranges)
- Representation headers (Content-Type: text/html; charset=utf-8, Content-Encoding: gzip, Last-Modified: Wed, 10 Aug 2016, 05:38:31 GMT)


3. Body
- not all responses have one
- Three categories:
  - Single-resource bodies, consisting of a single file of known length, defined by the two headers: Content-Type and Content-Length.
  - Single-resource bodies, consisting of a single file of unknown length, encoded by chunks with Transfer-Encoding set to chunked.
  - Multiple-resource bodies, consisting of a multipart body, each containing a different section of information. These are relatively rare.

<br>

###  Why should you ignore the `node_modules` folder in `.gitignore` ?

The node_modules folder contains all the module files of the project dependencies and can be several hundred MBs big with many thousand files. It's unnecessary to track it with GIT, because the package.json file contains all the necessary data to rebuild the folder by installing all the dependencies with "npm i".

<br>

## Rest API: Serve and Fetch

###  Why is it recommend for a developer to use the http methods `get`, `put`, `delete` ?

GET, PUT and DELETE are all standard HTTP methods, and it is recommended to use these and the others, because they cover all scenarios necessary that might be needed in the interaction between a client and a server. There is usually no need to invent new methods, those might just confuse other developers and it's most probably harder to maintain.

###  How does a `POST` request look like when it is made from a web browser (on the front end written) ?

```JS
const requestOptions = {
    method: 'POST',
    body: JSON.stringify(myOrder),
    headers: { 'Content-Type': 'application/json' },
};

fetch('/api/order', requestOptions)
            .then(response => "dosomething")
            .catch(error => console.log('error', error));
```

<br>

###  What is an API?

API stands for Application Programming Interface, it provides an interface for two or more computer programs to communicate with each other. An API specification is a document of standard that describes how to build or use such an interface. One purpose of APIs is to hide the internal details of how a system works, exposing only those parts a programmer will find useful and keeping them consistent even if the internal details later change. An API may be custom-built for a particular pair of systems, or it may be a shared standard allowing interoperability among many systems. The term API is often used to refer to web APIs, which allow communication between computers that are joined by the internet. There are also APIs for programming languages, software libraries, computer operating systems, and computer hardware.

<br>

###  What is REST API?

A REST (REpresentational State Transfer) API is a software architectural style that describes a uniform interface between physically separate components, often across the Internet in a client-server architecture. It has the following guiding principles:
- Uniform interface: 
  - Identification of resources
  - Manipulation of resources through representations
  - Self-descriptive messages
  - Hypermedia as the engine of application state
- Client-server architecture > Separation of concerns of client & server (user interface vs data storage)
- Stateless: each request from client to server must contain all the information necessary to understand and complete the request
- Cacheable: if the response is cacheable, client application gets the right to reuse the response data later for equivalent requests for a specified period of time
- Layered system: each component cannot see beyond the immediate layer they are interacting with
- Code on demand (optional): downloading and executing code in the form of applets or sripts (server provides script, client runs it)

RESTful:
- All CRUD methods on the same endpoint / CRUD for all resources
- Stateless: Server does not store information, request contains all information

<br>

###  What is JSON and how do we use it?

JSON (JavaScript Object Notation) is an open standard file format and data interchange format that uses human-readable text to store and transmit data objects consisting of attribute (key) and value pairs and arrays. It is a common data format with diverse uses in electronic data interchange, including that of web applications with servers. <br> <br>
JSON is a language-independent data format. It was derived from JavaScript, but many modern programming languages include code to generate and parse JSON-format data. JSON filenames use the extension .json. Any valid JSON file is a valid JavaScript (.js) file, even though it makes no changes to a web page on its own.

<br>

###  What is API versioning ?

API versioning is the practice of managing changes to an API and ensuring that these changes are made without disrupting clients. A good API versioning strategy clearly communicates the changes made and allows API consumers to decide when to upgrade to the latest version at their own pace.

Running parallel API versions, so services remain compatible.

<br>

###  Give 3 examples of HTTP response status codes ? Explain what each number means.

100: Continue <br>
200: OK <br>
302: Found <br>
304: Not modified <br>
400: Bad request <br>
403: Forbidden <br>
404: Not found <br>
418: I'm a teapot <br>
500: Internal server error <br>
502: Bad gateway <br>

<br>

## Advanced JavaScript

###  How does the `ternary operator` looks like in javascript?
The ternary operator syntax looks like this:

```JS
condition ? true : false;
return myNumber !== 2 ? myNumber === 3 ? 'The number is 3' : 'The number is neither 2 nor 3' : 'The number is 2';
return userScore + didUserWin ? 1 : 0;
```

<br>

###  How to import a function from another module in JavaScript?

```JS
import { useState } from "react";
import Header from './components/Header';
import myFunction from 'module';
```

<br>

###  What is a shallow copy on an object?

A shallow copy of an object is a copy whose properties share the same references (point to the same underlying values / memory) as those of the source object from which the copy was made.

<br>

###  What is a callback function? Tell some examples of its usage.

A callback function is a function that is passed into another piece of code as an argument. The code is expected to invoke the callback function as part of its routine. A callback function can both be a named or an anonymous function. <br>
One of the most frequent use of a callback function is in event listeners and http server logic.
For example:
```JS
const clickHandler = (e) => {
  someValue = e.target.value;
}

document.getElementById('button').addEventListener('click', clickHandler);
document.getElementById('button2').addEventListener('click', () => console.log('Callback fired'));
```

Both clickHandler and anonymous console.log functions are callback functions.

<br>

###  What is object destructuring in javascript?

Destructuring is a JavaScript expression that allows us to extract data from arrays, objects, and maps and set them into new, distinct variables. Destructuring allows us to extract multiple properties, or items, from an array​ at a time. To destructure objects we use { } with the exact name of what we have in the object.

Syntax:
```JS
let {variable1, variable2} = {variable1: 'value1', variable2: 'value2', variable3: 'value3};
// console.log(variable1) --> value1
// console.log(variable2) --> value2

const employee = {
  firstName: 'Jon',
  lastName: 'Snow',
  dateOfBirth: 1990
}
//age defined as default 33, if employee has age property, the default value will get overwritten
const {firstName: fn, lastName, dateOfBirth: dob, currentAge: age = 33} = employee;
console.log(fn, lastName, dob, age); // -> expected output: Jon Snow 1990 33
```

<br>

###  What is array destructuring in javascript?

Destructuring is a JavaScript expression that allows us to extract data from arrays, objects, and maps and set them into new, distinct variables. Destructuring allows us to extract multiple properties, or items, from an array​ at a time. To destructure arrays we use [ ] to store the variable name which will be assigned to the name of the array storing the element.

```JS
const array = [1, 2, 3, 4, 5, 6, 7];
const [var1, var2, var3] = array;
console.log(var1, var2, var3) // -> expected output: "1 2 3"

//swap position of variables in an array:
const edibles = ["food", "fruits"];

let [positionOne, positionTwo] = edibles;
console.log(positionOne, positionTwo); //expected output: "food fruits"

[positionOne, positionTwo] = [positionTwo, positionOne];
console.log(positionOne, positionTwo); //expected output: "fruits food"
```

<br>

###  What is the spread operator in `js` ?
The JavaScript spread operator (...) allows us to quickly copy all or part of an existing array or object into another array or object.
It takes in an iterable (e.g an array) and expands it into individual elements.
The spread operator is commonly used to make deep copies of JS objects. When we have nested arrays or nested data in an object, the spread operator makes a deep copy of top-level data and a shallow copy of the nested data. Using this operator makes the code concise and enhances its readability.

```JS
const numbersOne = [1, 2, 3];
const numbersTwo = [4, 5, 6];
const numbersCombined = [...numbersOne, ...numbersTwo];

const numbers = [1, 2, 3, 4, 5, 6];
const deepCopy = [...numbers];
const [one, two, ...rest] = numbers;

console.log(numbers); // -> [1, 2, 3, 4, 5, 6]
console.log(...numbers); // -> 1 2 3 4 5 6

const myVehicle = {
  brand: 'Ford',
  model: 'Mustang',
  color: 'red'
}

const updateMyVehicle = {
  type: 'car',
  year: 2021, 
  color: 'yellow'
}

const myUpdatedVehicle = {...myVehicle, ...updateMyVehicle}
```

It can also be used to pass the elements of an array as arguments of a function.

```JS
function sum(a, b) {
  return a + b;
}

const array = [2, 3];
console.log(sum(...array)); // -> 5

```

<br>

###  What are the differences between the `arrow` function and the regular `function`?

Differences:
- arrow function has implicite return,
- in arrow function, { } are not required if it's a one line function,
- "arguments" keyword is accessible in regular function, not in arrow function (...args has to be used in argument and inside)
- arrow function parameters need to be unique, not the case for regular function
- regular function can be called with constructor (function add(a,b) {}; let sum = new add(2,3))


```JS
const add = function(x, y) {
    return x + y;
};
const add = (x, y) =>  x + y;
```

"this" is handled differently, arrow function does not have its own this context, while regular function has:
```JS
var name = "Suprabha"
let newObject = {
    name : "supi",
    arrowFunc: () => {
        console.log(this.name); 
    },
    regularFunc() {
        console.log(this.name); 
    }   
}
newObject.arrowFunc(); // Suprabha
newObject.regularFunc(); // supi
```

<br>

###  What is the `import` keyword used for?
The `import` keyword is used to import bindings that are exported by another module.
- `import` is a new keyword that is used to import modules in ECMAScript 6 (ES6)
- `import` is an asynchronous operation, so the script will not be blocked while the module is loading.
- `import` can be used to import both modules and individual exports from those modules
<br>

###  What is the `required` used for?
The `require()` function is used to load a module in a Node.js application.
- `require` is a function used to import modules in Node.js,
- `require` is a synchronous operation and will block the execution of the script until the module is loaded and ready to be used,
- `require` can only be used to import modules
In Node.js - require() is a built-in function for including external modules that exist in separate files. The statement reads a JavaScript file, executes it, and then returns the exported object
<br>

###  What are template literals?
Template literals are literals delimited with backtick ( \` ) characters, allowing for multi-line strings, string interpolation with embedded expressions by inputting expression in "`${ }`", and special constructs called tagged templates.

```JS
const myName = 'Rudi';
console.log(`Hello ${Rudi}, this is a template literal`); // -> output: "Hello Rudi, this is a template literal
```
<br>

## Testing basics

###  What is code coverage? Why is it used?
Code coverage is a metric that measures the percentage of code that is executed by tests. It quantifies how much of the source code is exercised by the test suite. Code coverage is used to assess the thoroughness of testing efforts and identify areas of the codebase that are not adequately covered by tests. It helps developers gauge the effectiveness and completeness of their test suite. By analyzing code coverage reports, developers can identify untested or under-tested code, increasing their confidence in the reliability and correctness of their software. Higher code coverage often indicates a lower probability of undetected bugs or issues in the codebase.
<br>

###  What is a test case? What is an assertion? Give examples!
A test case is a specific scenario or condition used to verify the behavior or functionality of a piece of code. It consists of a set of preconditions, inputs, and expected outcomes. Test cases are designed to test specific aspects of the codebase and ensure it functions as intended. 

An assertion, in the context of testing, is a statement that checks whether a specific condition is true or false. It is used to validate expected behavior. Assertions are typically used to compare actual results against expected results.

Here's an example in JavaScript:

```javascript
// Test case
function add(a, b) {
  return a + b;
}

// Assertion
console.assert(add(2, 3) === 5, 'Addition failed!');
```

In this example, the test case defines the `add` function, which adds two numbers. The assertion verifies that calling `add(2, 3)` equals `5`. If the assertion fails, it will log the error message "Addition failed!" to the console, indicating an issue with the implementation.
<br>

###  What are the unit testing best practices? (Eg. how many assertion should a test case contain?)
Unit testing best practices include:

1. **Single Responsibility**: Each test case should focus on testing a single behavior or functionality, ensuring clarity and maintainability.

2. **Clear and Descriptive Names**: Test case names should be expressive and descriptive, highlighting the purpose and expected outcome of the test.

3. **Isolation**: Tests should be independent and isolated from each other, avoiding dependencies on external resources or other test cases.

4. **Minimal Assertions**: A test case should ideally contain a single logical assertion. However, multiple assertions are acceptable as long as they are tightly related and test the same behavior.

5. **Test Coverage**: Aim for comprehensive coverage by testing various scenarios and edge cases to validate different aspects of the code.

6. **Setup and Teardown**: Use setup and teardown methods to prepare the required environment for each test and clean up any resources afterward.

7. **Test Maintainability**: Keep tests simple, concise, and easy to understand, ensuring they remain maintainable as the codebase evolves.

While there is no strict rule on the number of assertions per test case, it is generally recommended to keep it to a minimum to improve test readability and maintainability. However, striking a balance between clarity and granularity is essential, and sometimes multiple assertions are necessary to adequately validate the desired behavior.
<br>

###  What is arrange/act/assert pattern?
The Arrange/Act/Assert (AAA) pattern is a widely used structure for organizing unit tests. It provides a clear and systematic way to structure test cases. In the Arrange phase, the necessary preconditions and test setup are established, including initializing objects and setting up any required data. The Act phase involves executing the specific behavior or method being tested. Finally, in the Assert phase, the expected outcome is verified by asserting against the actual results obtained from the Act phase. The AAA pattern helps to improve the readability, maintainability, and consistency of unit tests, making it easier to understand the purpose and flow of each test case.
<br>

###  How do you test asynchronous code with `jest` ?
In Jest, testing asynchronous code can be done using a variety of techniques. One common approach is to use the `async/await` syntax or the `Promise` API in combination with Jest's `expect` and `resolves/rejects` matchers. By using `async/await` or returning a promise, you can await asynchronous operations and then make assertions on the resolved or rejected values. Additionally, Jest provides the `done` callback to handle testing asynchronous functions that use callbacks. This allows you to inform Jest when the async code has completed. These techniques ensure that your tests correctly handle and validate the behavior of asynchronous operations in a controlled and reliable manner.
<br>

###  What is `setup` & `teardown` in jest ?
In Jest, `setup` and `teardown` refer to the lifecycle methods that allow you to perform setup and cleanup operations before and after running test cases. 

The `setup` phase, also known as the "before" phase, is where you can configure the necessary environment, initialize variables, or set up any required resources before executing the test cases. It runs once before every test case or test suite.

The `teardown` phase, also known as the "after" phase, is where you can perform cleanup operations, release resources, or reset any modifications made during the test. It runs once after every test case or test suite.

By utilizing `setup` and `teardown` methods, you can ensure that each test case starts with a consistent environment and is cleaned up properly afterward, promoting test isolation and reliability.
<br>

###  Give an example when you would use in `jest` the `toBe` & `toEqual` assertions.
In Jest, the `toBe` and `toEqual` assertions are commonly used to compare values in test cases.

The `toBe` assertion is used to compare strict equality between two values, checking if they are the exact same value in memory. It is typically used for primitive data types such as numbers, booleans, or strings. For example:

```javascript
expect(5).toBe(5);
expect(true).toBe(true);
expect('hello').toBe('hello');
```

On the other hand, the `toEqual` assertion is used to compare the equality of values based on their content or structure. It performs a deep equality check, making it suitable for comparing objects, arrays, or complex data structures. For example:

```javascript
const expectedArray = [1, 2, 3];
const actualArray = [1, 2, 3];
expect(actualArray).toEqual(expectedArray);

const expectedObject = { name: 'John', age: 25 };
const actualObject = { name: 'John', age: 25 };
expect(actualObject).toEqual(expectedObject);
```

By utilizing `toBe` and `toEqual` assertions appropriately, you can ensure that your tests accurately compare values based on the desired criteria, whether it's strict equality or content-based equality.
<br>

## React basics

###  What benefits does it bring for a developer to use `components` (opposed of writing all the code in a single file) ?

1. Reusability
  A component is self-contained, and can be used many times over.

2. Testability
  Much easier to test a component individually.

3. Efficiency
  A central library makes development faster.

4. Consistency
  Building from the same components, having the same high quality.

5. Maintainability
  Changing a component is easier.


###  What is the difference between Element and Component?

React Element is a simple object that describes a DOM node and its attributes or properties you can say. It is an immutable description object and you can not apply any methods on it, for example:
```JS
<button class="blue"></button>
```

<br>

React Component is a function or class that accepts an input and returns a React element. It has to keep references to its DOM nodes and to the instances of the child components. For example:
```JS
const SignIn = () => (
  <div>
   <p>Sign In</p>
   <button>Continue</button>
   <button color='blue'>Cancel</button>
  </div>
);
```

<br>

###  How do you pass values between components in `react`?

It's possible to pass values or functions from a parent component to a child component by passing it to the child via a property.
The child has access the properties in their argument. For example:

```JS
function App() {
    const myName = 'Rudi';
    const yourName = 'Boti';

    return (
        <div className="root">
            <Header name={myName}/>
            <Header name={yourName}/>
        </div>
    )
}
```
<br>

```JS
const Header = ({name}) => {
    return (
        <div className="header">
              User's name is: {name};
        </div>
    );
}
```

<br>

###  What is `key` prop?

If the `key` attribute is present, React uses it as a way to identify an element of the same type among its siblings during re-renders.
If the same item has the same id between rerenders, the performance is higher, than when with a changing id (eg. sorting). <br>
With index key:<br>
<img src="https://www.developerway.com/assets/react-key-attribute/index-based-sorted-list.png" alt="alt text" title="image Title" width="400"/>
<br>
With unique id:<br>
<img src="https://www.developerway.com/assets/react-key-attribute/id-based-sorted.png" alt="alt text" title="image Title" width="400"/>
<br>
https://www.developerway.com/posts/react-key-attribute

<br>

###  How does a child component pass data to it's parent component ?

There is no direct way to pass data from the child to the parent component, but there are workarounds. <br>
The most common one is to pass a handler function from the parent to the child component that accepts an argument which is the data from the child component.<br>
This can be better illustrated with an example.

```JS
const Parent = () => {
  const [message, setMessage] = React.useState("Hello World");
  const chooseMessage = (message) => {
    setMessage(message);
  };
  return (
    <div>
      <h1>{message}</h1>
      <Child chooseMessage={chooseMessage} />
    </div>
  );
};

const Child = ({ chooseMessage }) => {
  let msg = 'Goodbye';
  return (
    <div>
      <button onClick={() => chooseMessage(msg)}>Change Message</button>
    </div>
  );
};
```

<br>

###  Write the code to create in JSX an HTML DIV element that has the innerText the contents of the variable `let name = 'Andrew'`
```JS
let name = "Andrew";
return (
   <div> {name} </div>
)

```
<br>

###  Write the code to create in JSX an unordered list from the array `let names = ["Mathew", "John", "Maverik"]`
```JS
let names = ["Mathew", "John", "Maverik"];
return (
  <ul>
  {names.map((name,index) => <li key={index}>{name}</li>}
  </ul>
)

```
<br>

###  Write the code to set the background color red of a div in JSX.
```JS
return (
<div style={{backgroundColor: "red"}}>
  Red background
</div>
)
```
<br>

## Testing react

###  What are unit tests, integration tests? What is the major difference between these two?

From ChatGPT:
Unit tests are used to test individual units of code, such as functions or methods, in isolation from the rest of the system. These tests are typically written by developers and are used to ensure that the individual units of code are working correctly and are free of bugs. Unit tests should be small, fast and atomic, they should cover only the unit of code they are assigned to test.

Integration tests, on the other hand, test how different units of code interact with each other. These tests are used to ensure that the different parts of the system are working together correctly and that there are no bugs or issues when the different units of code are integrated. Integration tests are more complex and time-consuming than unit tests, they should cover multiple units and they test the whole system behavior.

The main difference between unit tests and integration tests is the scope of what is being tested. Unit tests focus on small, isolated units of code, whereas integration tests focus on how different units of code interact with each other. Unit tests are usually faster and simpler to write, but integration tests are necessary to ensure that the whole system is working correctly.

Unit tests are important for early detecting of errors or bugs and to make code more reliable, integration tests are important for early detecting of errors or bugs between the different components or systems of the whole software.

<br>

###  What is unit testing?
Unit testing is a software testing method in which individual units or components of a software application are tested in isolation from the rest of the system. These units are typically small, self-contained parts of the code, such as functions or methods, and they are tested to ensure that they are working correctly and are free of bugs.

Unit tests are typically automated and are executed by developers as they write the code, or by a continuous integration system. The goal of unit testing is to validate that each unit of the software application is working as intended. It can help detect bugs early, and makes it easy to maintain and refactor the code.

Unit tests are typically small, fast, and atomic, they should cover only the unit of code they are assigned to test, usually mock other dependencies to isolate the functionality of the unit.

Unit tests are an essential part of the software development process, especially in an Agile or Test-Driven Development (TDD) approach. They help ensure that the code is working as expected and that any changes made to the code don't introduce new bugs or break existing functionality.


<br>

###  What does `mocking` mean from a testing perspective ? Give an example when you would use it.
In software testing, mocking refers to the technique of creating simulated objects or functions that mimic the behavior of real components in order to isolate and test specific parts of a system. These mock objects or functions allow developers to control and manipulate their behavior during testing, making it easier to verify the functionality and interactions of other system components. For example, in unit testing, a developer might create a mock database object to simulate database operations and test the behavior of a particular module without relying on a real database connection, improving test efficiency and isolating potential issues.
<br>

###  How do you test that function was called `at least` 2 times using `jest` ?
In Jest, you can test if a function was called at least twice using the `jest.spyOn` method and the `toHaveBeenCalled` matcher in conjunction with the `toBeGreaterThanOrEqual` matcher. First, you create a spy on the function you want to test, then you invoke the function multiple times, and finally, you assert that the spy has been called at least twice. Here's an example:

```javascript
const myFunction = jest.fn();

// Invoke myFunction multiple times

expect(myFunction).toHaveBeenCalledTimes(expect.toBeGreaterThanOrEqual(2));
```

This test ensures that `myFunction` has been called at least twice by using the `toHaveBeenCalledTimes` matcher in combination with the `toBeGreaterThanOrEqual` matcher and the desired minimum count of 2.
<br>

###  Name 4 benefits a developer gets from writing tests.
Writing tests offers several benefits for developers:

1. **Improved Code Quality:** Tests help identify bugs and errors early in the development process, leading to higher code quality. By writing tests, developers can verify that their code behaves as expected and meets the desired functionality.

2. **Enhanced Code Maintainability:** Tests act as documentation for the expected behavior of code. When developers revisit their codebase or collaborate with others, tests serve as a guide, ensuring that changes or updates do not inadvertently introduce regressions or break existing functionality.

3. **Faster Debugging and Issue Resolution:** When a test fails, it indicates the presence of a problem. By having a comprehensive test suite, developers can quickly identify the source of issues, debug them efficiently, and resolve them promptly. This accelerates the development and debugging process.

4. **Increased Developer Confidence:** Writing tests provides developers with reassurance that their code is functioning correctly. Having a robust test suite allows them to make changes or refactor code with confidence, knowing that failing tests will alert them to any unintended consequences. This confidence encourages experimentation and promotes a more agile development process.

Overall, writing tests leads to more reliable, maintainable, and robust code, saving time and effort in the long run and increasing developer productivity.
<br>

## React patterns

###  What is the difference between Real DOM and Virtual DOM?
The Document Object Model (DOM) is a programming API for HTML and XML documents, it represents the structure of the document as a tree of nodes, allowing developers to access and manipulate the contents and layout of a web page.

A Real DOM is a actual representation of the web page, when any changes happens to the web page (such as adding or removing elements), the Real DOM needs to update the web page accordingly. Updating the Real DOM can be an expensive operation, especially when the page contains many elements or the updates need to happen frequently.

A Virtual DOM is a lightweight, in-memory representation of the web page. It serves as an intermediary between the Real DOM and the JavaScript code that updates the page. When changes are made to the page, the Virtual DOM updates first and then it calculates the difference between the previous and the next state, this is called Reconciliation. After that, it updates the Real DOM with the minimal number of changes needed.

This approach can greatly improve the performance of web applications because it reduces the number of changes that need to be made to the Real DOM, and thus reduces the number of expensive update operations.

React uses Virtual DOM to improve the performance of its components. When a component's state changes, React will update its corresponding Virtual DOM, and then compare it to the previous version to determine the minimal set of updates that need to be made to the Real DOM. This approach makes it possible to efficiently update complex, dynamic web pages with minimal overhead.

In short, Real DOM is actual representation of the web page and Virtual DOM is a lightweight representation of it, which helps to calculate the most optimal changes to the real DOM.

<br>

###  When adding an item to an array, why is it necessary to pass a new array to the `useState` hook ?

Because in JS an array is stored by reference and React will not detect a change if the content of the array is changed, but the reference is not. If a copied array is set, then the reference changes and React correctly updates the dom.

###  Describe what techniques or tools you use to debug a react app.

The techniques include:

- strategic console logging,
- React developer tools (installed as Chrome extension),
- using Strict mode,
- debugging tool in browser window

###  What is the difference between a react `class` component & a `functional` component ?

A functional component is just a plain JavaScript function which accepts props as an argument and returns a React element. It is a newer addition to React. A class component is older and has different methods than functional components. In classes lifecycle of components is managed stricter, using of states is more cumbersome.

###  Name 3 lifecycle states in a react `functional` component.

Mounting, updating, unmounting.

###  What is conditional rendering in `react` ? Give an example.

Conditional rendering in React works the same way conditions work in JavaScript. A component can be rendered or not based on the value of a variable or state by adding logic into the code, using "if", the ternary operator or other conditional. An example:

```JS
const Greeting = (props) => {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
}

const Details = (props) => {
  const isShown = props.isShown;
  return (
    <div>
    <Header />
    <Title />
    {isShown && <Content />}
    <Footer />
    </div>
  )
}
```

###  Write the code that prints to the console `component destroyed` when the component it is part of is removed from the DOM tree.

```JS

const Component = () {

  useEffect(() => {  

    return () => {
      console.log('component destroyed');
    }
  })

return (
  <div>
    Some code here maybe
  </div>
)
}

```

###  Why is there an infinite loop in this code

UseEffect does not have a dependency array, so it is run every time the site rerenders, and in the useEffect a state is updated, triggering a rerender. So every useEffect triggers a state change, which triggers a rerender and every rerender, useEffect runs again.

```JS
function App() {
  const [count, setCount] = useState(0); //initial value of this 
  useEffect(() => {
    setCount((count) => count + 1); //increment this Hook
  }); //no dependency array.
  return (
    <div className="App">
      <p> value of count: {count} </p>
    </div>
  );
}
```
###  Why is there an infinite loop in this code

In the main app, a state update triggers a rerender, which triggers a state update, and so forth.

```JS
  async function App() {
  const [count, setCount] = useState("");
  setCount(count + 1);
  return (
    <div className="App">
      <p> value of count: {count} </p>
    </div>
  );
}
```

<br>

## Mongo & mongoose

###  What is a database schema ?

A database Schema is the blueprint of a data structure, of a document that gets stored into a MongoDB collection. The data structure is defined as an object with key-value pairs, the values being the type of data (eg. String, Number, Date, Boolean). The value can be an array or an other Object. There are special keys as well, e.g. required that lets Mongoose enforce some rules so that the stored data has all the necessary information.

###  Why is the `id` unique in a database ?

An id is unique so that any two records can be distinguished from each other, even when all other values are identical.

###  What are the advatanges & disadvatages of using `lean()` function in a mongo query ?

The `lean()` method enhances the performance of the `find()`, because it returns plain javascript data, while the find return mongoose documents that have "mongoose magic" (setters, getters, save method) attached to them.

###  Write the code to store the object `{name: "Andrew", age: 10}` to a mongo database. You can ignore the part of connection parameters.

```JS
const mongoose = require('mongoose');
const userSchema = new mongoose.Schema({
  name: String,
  age: Number
})
module.exports = mongoose.model('User', userSchema)

//do I need the export and the import???

const User = require('./User');

User.insertOne({name: "Andrew", age: 10})
  .then(data => console.log(data))
  .catch(err => console.log(err));
```

###  Write the code to delete from a mongo database all employees that are over 18 years. The scheme for an employee is `{name: string, age: int}`. You can ignore the part of connection parameters.

```JS
Employees.deleteMany({age: {$gt: 18}})
  .then(data => console.log(data))
  .catch(err => console.log(err));
```

###  Write the code to display in the console from a mongo database the employees who are over 18 years. The scheme for an employee is `{name: string, age: int}`. You can ignore the part of connection parameters.

```JS
Employees.find({age: {$gt: 18}})
  .then(data => console.log(data))
  .catch(err => console.log(err));
```

###  Write the code to update from a mongo database the employees with name='John' and set the new age to 8. The scheme for an employee is `{name: string, age: int}`. You can ignore the part of connection parameters.

```JS
Employees.updateMany({name: "John"}, {$set: {age: 8}})
  .then(data => console.log(data))
  .catch(err => console.log(err));
```

<br>

## Authentication (cookies + google)
###  How to properly store passwords?
Storing passwords in a secure manner involves a few key considerations.

1. Hashing: Instead of storing passwords in plaintext, they should be hashed. Hashing is a one-way process that converts a password into an irreversible string of characters. When a user logs in, their entered password is hashed and compared to the stored hashed password.

2. Salt: To further enhance security, it's recommended to use a salt in the hashing process. A salt is a random string of characters unique to each user. It is concatenated with the password before hashing. Salting helps defend against attacks such as rainbow tables and increases the complexity of cracking passwords.

3. Strong hashing algorithm: Choose a strong, industry-standard hashing algorithm such as bcrypt, Argon2, or scrypt. These algorithms are specifically designed for password hashing and are more resistant to attacks compared to simple hashing functions like MD5 or SHA.

4. Iterations: To make the hashing process more time-consuming and resource-intensive for attackers, use a high number of iterations in the hashing algorithm. This slows down brute-force and dictionary attacks.

5. Secure storage: Ensure that the hashed passwords are stored securely. In a database, for example, use appropriate access controls and encryption to protect the stored passwords from unauthorized access.

6. Never store plaintext passwords: Never store passwords in plaintext or any reversible encryption format. Storing passwords in plaintext makes them easily readable if a security breach occurs.

7. Password reset mechanism: Implement a secure password reset mechanism that allows users to reset their passwords if they forget them. This mechanism should involve strong authentication and verification steps.

###  What is encryption and decryption?
Encryption is the process of converting plain, readable data (plaintext) into a scrambled, unreadable form (ciphertext) using an algorithm and a secret key. It ensures that the information is protected from unauthorized access during storage or transmission.

Decryption is the reverse process of encryption. It involves using the same algorithm and the corresponding secret key to convert the ciphertext back into plaintext, making the data readable and usable again.

###  What is hashing?
Hashing is a one-way process that converts a password into an irreversible string of characters. When a user logs in, their entered password is hashed and compared to the stored hashed password.
###  What is OAuth2?
OAuth2 (Open Authorization 2.0) is an open standard protocol that allows secure authorization and delegated access to user resources on behalf of a third-party application. It provides a framework for users to grant limited access to their protected resources, such as personal information or online accounts, without sharing their credentials (e.g., username and password) directly with the third-party application.

In OAuth2, there are typically three main entities involved:

* Resource Owner: This is the user who owns the protected resources and wants to grant access to them.

* Client: The application or service that requests access to the user's resources. This could be a web application, mobile app, or any other type of client.

* Authorization Server: The server that authenticates the resource owner and issues access tokens to the client. It verifies the identity of the user and their authorization to grant access to the requested resources.

The OAuth2 flow involves the following steps:

* The client requests authorization from the resource owner by redirecting them to the authorization server.

* The resource owner authenticates themselves with the authorization server.

* Once authenticated, the resource owner grants permission to the client to access their resources.

* The authorization server issues an access token to the client, which is a credential used to access the protected resources.

* The client can then use the access token to request and access the protected resources from the resource server (the server hosting the resources).

OAuth2 provides a secure and standardized way for users to grant access to their resources to third-party applications without sharing sensitive credentials. It is widely used by many popular online platforms, social networks, and APIs to enable secure integration and data access between different services and applications.

###  What is the difference between encryption and hashing? When would you use which?
Encryption and hashing are both cryptographic techniques, but they serve different purposes and have distinct characteristics. Here's a comparison between encryption and hashing:

Encryption:

* Purpose: Encryption is used to protect data confidentiality by transforming plaintext into ciphertext using an encryption algorithm and a secret key.
* Reversibility: Encryption is reversible. The ciphertext can be decrypted back to its original plaintext using the corresponding decryption algorithm and the secret key.
* Use case: Encryption is commonly used to secure sensitive data during storage or transmission. It's suitable for scenarios where the original data needs to be retrieved in its original form.
* Example: Encrypting a file, securing network communications using SSL/TLS.
Hashing:

* Purpose: Hashing is primarily used for data integrity and verification, rather than confidentiality. It converts data of any size into a fixed-length hash value using a hashing algorithm.
Irreversibility: Hashing is a one-way process, meaning the hash value cannot be converted back to its original data. The same input will always produce the same hash output.
* Use case: Hashing is often used for password storage, digital signatures, and verifying data integrity. It is suitable when you don't need to retrieve the original data but only need to compare hash values for verification.
* Example: Storing and verifying passwords, ensuring data integrity through hash-based message authentication codes (HMAC).

In summary, encryption is used to protect data confidentiality and is reversible, while hashing is used for data integrity verification and is irreversible. Encryption is suitable when you need to retrieve the original data, while hashing is appropriate when you only need to compare hash values or verify data integrity without needing the original data.

###  How/where would you store sensitive data (like db password, API key, ...) of your application?
Storing sensitive data, such as database passwords, API keys, or other credentials, requires careful consideration to ensure the security of your application. Here are some recommended practices:

* Environment Variables: Store sensitive data as environment variables in your application's deployment environment. This allows you to separate the configuration from the codebase and keeps sensitive information outside of version control. Most deployment platforms provide mechanisms for managing environment variables securely.

* Secrets Management Systems: Utilize dedicated secrets management systems such as HashiCorp Vault, AWS Secrets Manager, or Azure Key Vault. These systems provide secure storage and management of sensitive data, allowing you to retrieve credentials programmatically when needed.

* Encryption: If you need to store sensitive data within your application or configuration files, consider encrypting the data. Store the encryption key securely, such as in an environment variable or a hardware security module (HSM). Decrypt the data only at runtime when required.

* Restricted Access: Limit access to sensitive data by ensuring only authorized individuals or systems can access it. Implement strong access controls and permissions, and regularly review and update access privileges to minimize the risk of unauthorized access.

* Least Privilege Principle: Apply the principle of least privilege, granting access rights to sensitive data only to those individuals or components that require it. Avoid using privileged credentials or API keys in places where they are unnecessary.

* Regularly Rotate Credentials: Regularly change and rotate sensitive credentials such as passwords and API keys. This helps mitigate the impact of a potential security breach or unauthorized access.

* Audit Trails and Monitoring: Implement logging and monitoring mechanisms to track access to sensitive data and detect any unusual or unauthorized activities. Monitor for any security-related events and anomalies.

* Secure Data Transmission: When transmitting sensitive data over networks, ensure the use of secure protocols such as HTTPS/SSL/TLS to encrypt the data in transit and prevent eavesdropping.

Remember, security is a multi-layered approach, and the specific practices may vary based on your application's architecture and the security requirements of your environment. It is also important to keep up with security best practices, stay informed about any vulnerabilities, and regularly update and patch your systems.

###  What would you use a session for?
Sessions are used to maintain stateful interactions between a user and a web application. A session represents a unique connection or interaction between a user and the application during a specific period of time. Here are some common use cases for sessions:

* User Authentication: Sessions are commonly used for user authentication and authorization. When a user logs in, their authentication credentials are validated, and a session is created to keep track of their logged-in state. The session allows the application to verify subsequent requests from the user and provide access to restricted resources.

* User Personalization: Sessions can be used to store user-specific preferences or settings. For example, an e-commerce application can use a session to remember a user's selected language, currency, or theme preference throughout their browsing session.

* Shopping Carts: Sessions are often utilized to manage shopping carts in e-commerce applications. The session stores information about the items a user has added to their cart, allowing them to navigate between pages while maintaining their selected items until they proceed to checkout or clear the cart.

* Form Data Persistence: Sessions can be used to retain form data when a user navigates between pages or in case of form submission errors. The session can store the form inputs, enabling the user to continue filling out the form without losing their progress.

* Tracking User Activity: Sessions can be utilized to track user activity, such as the pages they visit, actions they perform, or duration of their session. This information can be valuable for analytics, personalization, or security purposes.

* Access Control: Sessions can help enforce access control rules by associating a user's permissions or roles with their session. This allows the application to verify whether a user has the necessary privileges to perform certain actions or access specific resources.

It's important to note that sessions typically rely on cookies or unique session identifiers to maintain the session state between the client and the server. The server can associate the session data with the corresponding session identifier, allowing it to retrieve and update session information as needed.

The specific use cases for sessions may vary depending on the nature of the web application and its requirements.

### What would you use a cookie for?
Cookies are small text files stored on a user's computer or device by a web browser. They serve various purposes and are commonly used in web development. Here are some typical use cases for cookies:

* Session Management: Cookies are often used to manage sessions and maintain user state. A unique session identifier can be stored in a cookie, allowing the server to recognize and associate subsequent requests from the same user with their session. This enables features such as user authentication, personalized content, and remembering user preferences throughout a browsing session.

* User Authentication and Authorization: Cookies are utilized to store authentication tokens or session tokens, which validate a user's identity and authenticate them for subsequent requests. By storing an encrypted token in a cookie, the server can authenticate the user without requiring them to re-enter their credentials for each page or request.

* Personalization and User Preferences: Cookies can be used to remember user preferences, such as language settings, theme choices, or font sizes. This allows the website to customize the user experience based on their preferences, enhancing personalization.

* Shopping Carts and E-commerce: Cookies are commonly employed to manage shopping carts in e-commerce applications. The cart details, such as the selected items and quantities, can be stored in a cookie, enabling the user to add items to their cart and retain the selections as they navigate through the site.

* Tracking and Analytics: Cookies can be used to track user behavior and gather analytics data. By storing a unique identifier in a cookie, websites can track visits, page views, conversion rates, and other metrics. This information helps in analyzing user behavior, optimizing marketing campaigns, and improving website performance.

* Advertising and Remarketing: Cookies are utilized in online advertising to track user interests and deliver targeted ads. Ad networks and advertisers may use cookies to gather information about a user's browsing habits and display relevant advertisements based on their preferences and previous interactions.

* Cross-Site Request Forgery (CSRF) Protection: Cookies can be used to implement CSRF protection mechanisms. A unique token stored in a cookie can be compared with a token sent in a form submission to verify the authenticity of the request and protect against CSRF attacks.

It's important to note that while cookies provide various functionalities, their usage should comply with privacy regulations and respect user consent. Websites should provide clear information about their use of cookies and allow users to manage their cookie preferences.

<br>

## Mern stack

### What does `MERN` stand for in the context of web development ?

MongoDB, Express, React, Node.

### What is routing in the context of a `react` app ?

Solve routing on front end. Loading different components on different "subdomains".

### What is routing in the context of an `express` app ?

API endpoints

### What is `CORS` policy ?

The Cross-Origin Resource Sharing (CORS) mechanism supports secure cross-origin requests and data transfers between browsers and servers. 
CORS is an HTTP-header based mechanism that allows a server to indicate any origins (domain, scheme, or port) other than its own from which a browser should permit loading resources.
<br>
For security reasons, browsers restrict cross-origin HTTP requests initiated from scripts. For example, XMLHttpRequest and the Fetch API follow the same-origin policy. This means that a web application using those APIs can only request resources from the same origin the application was loaded from unless the response from other origins includes the right CORS headers.
In most cases, browsers will make a “preflight” request to the host server to ensure the actual request will work. This is another function of CORS.

<br>

### What advantages does a developer have for using `bootstrap` or `material ui` ?

Both Bootstrap and Material-UI are popular front-end frameworks that provide pre-designed components and styles to help developers build responsive and visually appealing web applications.
* wide range of ready-to-use UI components
* responsive and optimized design for different screen sizes and devices
* easy to use and integrate into React-based projects
Both frameworks offer advantages in terms of development speed, consistent design, and customization.

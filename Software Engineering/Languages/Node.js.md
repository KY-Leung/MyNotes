## Node.js

* Server-side javascript
* uses MVC
* single-threaded ( the processing of one command at a time) using non-blocking I/O calls (code that doesn't block execution, `fetch` is a non-blocking operation as it does not stall code from execution)
* supports thousands of concurrent connections
* alternative of PHP
* great for +real-time

### What can we build with Node.js

* REST APIs & Backend applications
* Real-Time Services (Chat, Games, etc)
* Blogs, Content Management System, Social applications
* Utilities & Tools
* Anything that is not CPU-intensive

### NPM: The Node Package Manager

To install node programs / modules

A set of publicly available, reusable components, available through easy installation via an online repository, with version and dependency management

### Synchronous

Code executing in sequence.

```javascript
// Synchronous: 1,2,3
alert(1);
alert(2);
alert(3);
```

### Asynchronous

Execution that doesn't run in the sequence it appears in the code.

```javascript
// Asynchronous: 1,3,2
alert(1);
setTimeout(() => alert(2), 0);
alert(3);
```



### Blocking

Operations that block further execution until that operation finishes.  `localStorage` is a blocking operation as it stalls execution to read.

```javascript
// Blocking: 1,... 2
alert(1);
var value = localStorage.getItem('foo');
alert(2);
```

### Non-blocking

Code that doesn't block execution. `fetch` is a non-blocking operation as it does not stall `alert(3)` from execution.

```javascript
// Non-blocking: 1, 3,... 2
alert(1);
fetch('example.com').then(() => alert(2));
alert(3);
```



## Express

A web development framework

npm init (generate package.json file)

npm install express --save (add into package.json file)

or just run npm install

1. Importing modules

```javascript
var express = require('express');
var bodyParser = require('body-parser');
var path = require('path');
```

2. Initialize app

```javascript
var app = express();
```

3. Handle GET request; specify call back function taking in request & respond

```java
app get('/', function(req, res){
  res send('Hello World');
  res json(people); //print object in JSON format
})
```

4. Listen on port; specify port and call back function

```javascript
app listen(3000, function(){
  console log('Server Started on Port 3000...');
})
```

5. Restart the server if edited

   5.1 Ctrl + C to stop

   5.2 node app (to run server)

   5.3 localhost:3000

6. ​
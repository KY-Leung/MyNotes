## Key things about JavaScript

* case sensitive

* everything is an object

* statements are separated by semicolons

* Strings can be written with single or double quotes

* Variables created **without** the keyword **var**, are always global, even if they are created inside a function.

* document.getElementById in onclick()

* Accessing a function without () will return the code instead of the result

  ​

## Where to Insert JavaScript

```javascript
// JavaScript in <head>, <body>
<script>
var person = "John Doe", carName = "Volvo", price = 200;
var cars = ["Saab","Volvo","BMW"];
var person = {
    firstName : "John",
    lastName  : "Doe",
    age       : 50,
    fullName  : function() {
       return this.firstName + " " + this.lastName;
    }
};

printDemo('Good Morning!');

function myFunction() {
  person = person.firstName + " " + person.lastName
}

function printDemo(txt) { 
    document.getElementById("demo").innerHTML = txt
} 
</script>

// JavaScript in an external file
<script src="myScript.js"></script>
```



## What can JavaScript do?

### Change HTML attribute

``` javascript
<button onclick="document.getElementById('myImage').src='pic_bulbon.gif'">Turn on the light</button>

<img id="myImage" src="pic_bulboff.gif" style="width:100px">
```

###  Change CSS style

```javascript
document.getElementById('demo').style.fontSize='35px
```

### HIde / Show HTML elements

```javascript
document.getElementById('demo').style.display='none'
document.getElementById('demo').style.display='block
```



## JavaScript Output

### Writing into HTML element

```javascript
document.getElementById("demo").innerHTML = 5 + 6;
```

### Writing into alert box

```javascript
window.alert("John" + " "  + "Doe");
```

### Writing into browser console

```javascript
console.log(5 + 6);
```



|                                | Example                    |
| ------------------------------ | -------------------------- |
| Find variable type             | typeof 3.14                |
| Find string length             | txt.length                 |
| Find text's first occurrence   | str.indexOf("locate")      |
| Search for a text in a string  | str.match(/ain/g)          |
| Replace characters in a string | str.replace("soft","hard") |
| Convert string to upper case   | text.toUpperCase()         |
| Convert string to lower case   | text.toLowerCase()         |
| Split a string into an array   | var arr = str.split(",");  |
| Random number between 0 to 1   | Math.random()              |

|         |                                          |
| ------- | ---------------------------------------- |
| onclick | <button onclick="this.innerHTML=Date()">The time is?</button> |



## [let, var, const](https://stackoverflow.com/a/11444416/414825)

|         | Scope          | Re-declarable | Updatable |
| ------- | -------------- | ------------- | --------- |
| `var`   | Function scope | Yes           | Yes       |
| `let`   | Block scope    | No            | Yes       |
| `const` | Block scope    | No            | No        |

> but properties of a `const` variable *can* change.
>
> **Analogy:** an object is like me. I’m not going to ever change, my entire life, but things about about me are going to change.



## Object Constrictor

Once you have an object constructor, you can create new objects of the same type:

```javascript
function person(first, last, age, eye) {
    this.firstName = first;
    this.lastName = last;
    this.age = age;
    this.eyeColor = eye;
}
// Object Initializers (Static)
myBrother = {firstName: "Dave", lastName: "Doe", age: 18, eyeColor: "black"};

var myFather = new person("John", "Doe", 50, "blue");
var myMother = new person("Sally", "Rally", 48, "green");
```



## Function

*bar is pointing to an object (function is an object)*

```javascript
function foo() {
  console.log("Function foo called");
}

var bar = function() {
  console.log("Function bar called");
}

foo();
bar();
```



### Function stored in a variable

```javascript
var x = function (a, b) {return a * b};
var z = x(4, 3);
```



### Self-Invoking Functions

> Invoked (started) automatically, without being called
>
> Function expressions will execute automatically if the expression is followed by ()
>
> You have to add parentheses around the function to indicate that it is a function expression

```javascript
(function () {
    var x = "Hello!!";      // I will invoke myself
})();
```





### Function Scoping

Javascript is not Block Scope ; does not create scope for blocks {}. It is Function Scope; create scope by using function

### Adding Methods to Our Objects

```javascript
function people(name, age) {
  this.name = name;
  this.age = age;
  this.yearsUntilRetire = yearsLeft;
}

function yearsLeft(){
  var numYears = 65 - this.age;
  return numYears;
}

var bucky = new people("Bucky Roberts", 24);
document.write(bucky.yearsUntilRetire());
```

* No () in object, () when calling 



### Nested Function

***Nested functions have access to the scope "above" them***

```javascript
function add() {
    var counter = 0;
    function plus() {counter += 1;}
    plus();    
    return counter; 
}
```



### Closure*

A function that remember its scope, even is called at different scope. It has pointers to the actual variables.

A JavaScript closure is a function that has a pointer reference to a free variable. A free variable is one that has fallen out of scope after its parent function has returned. However, if that outer function still has some reference to the free var (normally through a function that gets returned, or through a method property), the variable will not get garbage collected because it will have a non-zero reference count. Thus, from outside the function, we can still access the inner variable by means of the closure.

JS parent function variables are private/hidden and only accessible through the JS inner function variables which are public/accessible from outside the function

```javascript
function outer() {
  var a = "blah";
  
  function inner() {
    alert(a);
  }
  return inner;
}

var myClosure = outer();
myClosure();
```



### Prototype*

Prototype allows to add properties and methods to the object. 

***You shouldn't create a method in a object, because it will be loaded every time you create a new instance of that object. All instances share a single method thus saving some memory.*** This would be useful in large projects where you are creating lot's of instances of a single constructor function

If you create 5 different instances of player(), the attack property is created 5 times (even though they all do the exact same thing). If you use prototype, it is created once, and reused by all. If you modified the prototype, all the existing instances would reuse the new function. 

If you use a property, say player.protoype.energy = 100, ***it'll change it for every instances.***﻿

Let's say you are including a JavaScript library or Framework from an external source, one that you don't have direct control over. You can override or add to aspects of that class or object via prototype

```javascript
function Player(){
    this.name;
    this.hitpoints = 100;
    }
}

Player.prototype.heal = function(targetPlayer){
	targetPlayer.hitpoints += 5;
};

var p1 = new Player();
p1.name = "Conan";
p1.heal(p2);
```





## Global Namespace

Don't pollute the global namespace. Do not create multiple global variables. Create multiple global variables could possibly be overwritten or misconstrued somewhere.

As variables lose scope, they will be eligible for garbage collection. If they are scoped globally, then they will not be eligible for collection until the global namespace loses scope.

```javascript
var arra = [];
for (var i = 0; i < 2003000; i++) {
 arra.push(i * i + i);
}
```

Adding this to your global namespace should ad 10,000 kb of memory usage (win7 firefox) which will not be collected. Other browsers may handle this differently.

Whereas having that same code in a scope which goes out of scope like this Will allow `arra` to lose scope after the closure executes and be eligible for garbage collection.

```javascript
(function(){
 var arra = [];
 for (var i = 0; i < 2003000; i++) {
  arra.push(i * i + i);
 }
})();
```





## this (this current object)

In JavaScript, the thing called **this**, is the object that "owns" the JavaScript code.

The value of **this**, when used in a function, is the object that "owns" the function.

The value of **this**, when used in an object, is the object itself.

The **this** keyword in an object constructor does not have a value. It is only a substitute for the new object.

The value of **this** will become the new object when the constructor is used to create an object.

not a variable. It is a keyword. You cannot change the value of **this**.



## JSON

### Looping

```JAVASCRIPT
var myObj = { "name":"John", "age":30, "car":null };
for (x in myObj) {
  	// Through properties
    document.getElementById("demo").innerHTML += x + "<br>";
  
  	// Through property values
  	document.getElementById("demo").innerHTML += myObj[x] + "<br>";
}
```

### Create object with JSON String

``` javascript
var obj = JSON.parse('{ "name":"John", "age":30, "city":"New York"}');
```




## React.js

* JS Library for creating user interfaces with reusable components / widgets
* The V in MVC
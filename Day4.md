# Day 4: Functions, Events & Handlers

This README file summarizes the JavaScript lessons on Functions and Events & Handlers. **Function** is a reusable block of code that performs a specific task or set of tasks. **Events** refer to actions or occurrences that happen in the browser or on a webpage, often triggered by user interactions or system events.    

## Lesson Summary

In this lesson, we explored Functions, Events & Handlers in JavaScript. Here are the key points covered:

- What are Functions, their parameters & arguments & the returning values to them?
- What is Arrow Function?
- Scopes in JavaScript.
- What are Event Listeners & Event Object?

### Functions

values **are** things      

variables **point** to things     

functions **do** things       

```javascript
// declaring (creating) a function:
function half(x) {
    return x / 2;
}

// calling (using) a function:
const one = half(2);

//Parameters & Arguments   Some functions need more than one value to work
function add(x, y) {
    return x + y;
}
add(2,3);

//Some functions don't even need any values
function getRandomNumber() {
    return Math.random();
}
getRandomNumber();

//-parameters- are the inputs a function expects
//-arguments- are the actual values the function is called with
function add3(x, y, z) {
    console.log("My parameters are named x, y, z");
    console.log("I received the arguments", x, y, z);
    return x + y + z;
}
const sum = add3(4,5,6);

//Parameters should be named like variables, and behave like variables within the function body
function doesThisWork("literally a value") {
    return true;
}  // that code will give an error (SyntaxError: Unexpected string)
function howAboutThis(1weirdVariable!) {
    return true;
}  //that code will give an error (SyntaxError: Invalid or unexpected token)

//JS is pretty "loosey-goosey" about missing/extra arguments
getRandomNumber("unexpected")//js will ignore the extra argument


//A return statement specifies the function's output value
function square(x) {
    return x * x; 
}
const nine = square(3);// nine = 9

//Some functions don't return anything
function sayHello(name) {
    console.log("Oh hi, " + name + "!");
}
sayHello("Marc");// oh hi Marc !

//When there's no return the returned value is undefined
const hm = sayHello("Marc");// hm = undefined
```

#### Arrow Functions:
An **arrow function** (also known as a fat arrow function) is a concise way to write anonymous functions in JavaScript. It provides a shorter syntax compared to traditional function expressions, making the code more compact and often easier to read. Arrow functions were introduced in ECMAScript 6 (ES6) and have become widely used in modern JavaScript.    


```javascript
//arrow functions are expressions, we can assign them to a variable
const add = (x, y) => x + y;
// is equivalent to
function add(x, y) {
    return x + y;
}

//Arrow functions are great when we just want to return a value
function square(x) {
    return x*x;
}
// vs.
const square = (x) => x*x;

//For one-parameter functions, parentheses are optional
x => x*x
(x) => x*x

//For multiple parameters, parentheses are required
(firstName, lastName) => firstName + " " + lastName

//If we need to do more than just return a value, we can use curly braces for a "normal" function body.
//In that case, we still need a return
const addAndLog = (x, y) => {
    let sum = x + y; 
    console.log('The sum is', sum);
    return sum;
}
```

### Scope

In JS it doesn't just matter what variables we declare. It also matters where we declare them. Scope determines where variables are "in play"

```javascript
function declareBankruptcy() {
    let bankruptcy = true;
}
declareBankruptcy();
console.log(bankruptcy);// ReferenceError: bankruptcy is not defined

//Scopes are nested within the program
//The widest scope is the global scope
//Each function gets its own new scope within the scope where it was declared
let planet = "Jupiter";

function scopeOut() {
    let planet = "Mars";
    console.log("Inner planet:", planet);// Inner planet: Mars
}

scopeOut();
console.log("Outer planet:", planet);// Outer planet: Jupiter

//Within each scope, you can access variables declared in a wider scope (e.g. global scope)
//But not those declared in a narrower scope (e.g. function scope)
let globalVariable = "I live in global scope"; 
function narrowerScope() {
    console.log(globalVariable);//I live in global scope
    let localVariable = "I live in the function scope";
}
narrowerScope();
console.log(localVariable);// error

//Variables declared with let can be modified from within a narrower scope
//This can be useful, but also dangerous!
let feeling = "free";
function trap() {
    feeling = "boxedIn";
}
trap();
console.log(feeling);//boxedIn

```

### Events & Handlers

The web browser fires events when certain things happen on the page    
For example, when the user clicks somewhere on the page, a **click** event is fired   

We can detect events with JS using an event listener    
The **.addEventListener()** method lets us listen for events on a DOM element   
```javascript
document.addEventListener("click", () => {
    console.log("clicked")
});
```
.addEventListener() takes 2 parameters:

- The name of the event to listen to (e.g. "click")
- A handler function that JS calls when that event is fired on this element


JS passes an **event object** to the handler function with information about the event     

If we accept this as a parameter, we can use it to get details
```javascript
document.addEventListener("click", (event) => {
    console.log(event);
});

//event.target is the element the event fired on (in this case, which element was clicked)
document.addEventListener("click", (event) => {
    console.log(event.target);
});

```

"click" isn't the only type of event we can handle

- "dblclick"
- "mouseover"
- "mouseout"


## Coding Problems:

### [Global Scope and Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-scope-and-functions)

#### My Solution
```javascript
// Declare the myGlobal variable below this line
let myGlobal =10;

function fun1() {
  // Assign 5 to oopsGlobal here
oopsGlobal =5;
}

// Only change code above this line

function fun2() {
  let output = "";
  if (typeof myGlobal != "undefined") {
    output += "myGlobal: " + myGlobal;
  }
  if (typeof oopsGlobal != "undefined") {
    output += " oopsGlobal: " + oopsGlobal;
  }
  console.log(output);
}
```

### [Local Scope and Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/local-scope-and-functions)

#### My Solution
```javascript
function myLocalScope() {
  // Only change code below this line
let myVar = 10;
  console.log('inside myLocalScope', myVar);
}
myLocalScope();

// Run and check the console
// myVar is not defined outside of myLocalScope
console.log('outside myLocalScope', myVar);
```

### [Global vs. Local Scope in Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-vs--local-scope-in-functions)

#### My Solution
```javascript
// Setup
const outerWear = "T-Shirt";

function myOutfit() {
  // Only change code below this line
let outerWear ="sweater";
  // Only change code above this line
  return outerWear;
}

myOutfit();
```

### [Stand in Line](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/stand-in-line)

#### My Solution
```javascript
function nextInLine(arr, item) {
  // Only change code below this line
  arr.push(item);
  let removeditem = arr.shift();
  return removeditem;
  // Only change code above this line
}

// Setup
let testArr = [1, 2, 3, 4, 5];

// Display code
console.log("Before: " + JSON.stringify(testArr));
console.log(nextInLine(testArr, 6));
console.log("After: " + JSON.stringify(testArr));
```

# Day 8: Closures & Asynchronous JavaScript
This README file summarizes the JavaScript lesson on Closures & Asynchronous JavaScript.

## Lesson Summary

In this lesson, we explored Closures & Asynchronous JavaScript. Here are the key points covered:
- Closures & Function Closure
- Returning Functions & Returning Functions Memory
- Nested Function Scope
- Asynchronous in JavaScript
- Asynchronous Browser Features

### Closure

- Closure is the most esoteric of JavaScript concepts.
- Enables powerful pro-level functions like ‘once’ and ‘memoize’.
- Many JavaScript design patterns including the module pattern use closure.
- Build iterators, handle partial application and maintain state in an
asynchronous world.

```javascript
//Functions get a new memory every run/invocation
function multiplyBy2 (inputNumber){
const result = inputNumber*2;
return result;
}
const output = multiplyBy2(7);
const newOutput = multiplyBy2(10);

```
#### Functions with memories

- When our functions get called, we create a live store of data (local
memory/variable environment/state) for that function’s execution context.
- When the function finishes executing, its local memory is deleted (except the
returned value)
- But what if our functions could hold on to live data between executions?
- This would let our function definitions have an associated cache/persistent
memory
- But it all starts with us **returning a function from another function**

```javascript
//Functions can be returned from other functions in JavaScript
function createFunction() {
 function multiplyBy2 (num){
 return num*2;
 }
 return multiplyBy2;
}
const generatedFunc = createFunction();
const result = generatedFunc(3); // 6


//Calling a function in the same function call as it was defined
function outer (){
 let counter = 0;
 function incrementCounter (){
 counter ++;
 }
 incrementCounter();
}
outer();
//Where you define your functions determines what data it has access to when you call it

//Calling a function outside of the function call in which it was defined
function outer (){
 let counter = 0;
 function incrementCounter (){ counter ++; }
 return incrementCounter;
}
const myNewFunction = outer();
myNewFunction();
myNewFunction();

```

#### The bond
When a function is defined, it gets a bond to the surrounding Local Memory     
(“Variable Environment”) in which it has been defined.

#### The ‘backpack’
- We return incrementCounter’s code (function definition) out of outer into
global and give it a new name - myNewFunction
- We **maintain the bond to outer’s live local memory** - it gets ‘returned out’
attached on the back of incrementCounter’s function definition.
- So outer’s local memory is now stored attached to myNewFunction - even
though outer’s execution context is long gone
- When we run myNewFunction in global, it will first look in its own local
memory first (as we’d expect), but then in myNewFunction’s ‘backpack’    

**What can we call this ‘backpack’?**
- Closed over ‘Variable Environment’ (C.O.V.E.)
- Persistent Lexical Scope Referenced Data (P.L.S.R.D.)
- ‘Backpack’
- ‘Closure’
The ‘backpack’ (or ‘closure’) of live data is attached incrementCounter (then to
myNewFunction) through a hidden property known as [[scope]] which persists
when the inner function is returned out.

```javascript
//Let’s run outer again
function outer (){
 let counter = 0;
 function incrementCounter (){
 counter ++;
 }
 return incrementCounter;
}

function outer (){
 let counter = 0;
 function incrementCounter (){
 counter ++;
 }
 return incrementCounter;
}
```

**Individual backpacks**     
If we run 'outer' again and store the returned 'incrementCounter' function
definition in 'anotherFunction', this new incrementCounter function was created in
a new execution context and therefore has a brand new independent backpack


**Closure gives our functions persistent memories and
entirely new toolkit for writing professional code**     

**Helper functions**: Everyday professional helper functions like ‘once’ and ‘memoize’   
**Iterators and generators**: Which use lexical scoping and closure to achieve the
most contemporary patterns for handling data in JavaScript      
**Module pattern**: Preserve state for the life of an application without polluting the
global namespace         
**Asynchronous JavaScript**: Callbacks and Promises rely on closure to persist state
in an asynchronous environment      

### Promises, Async & the Event Loop
- Promises - the most signficant ES6 feature
- Asynchronicity - the feature that makes dynamic web applications possible
- The event loop - JavaScript’s triage
- Microtask queue, Callback queue and Web Browser features (APIs)

#### Asynchronicity is the backbone of modern web development in JavaScript yet...
JavaScript is:
- Single threaded (one command runs at a time)
- Synchronously executed (each line is run in order the code appears)
So what if we have a task:
- Accessing Twitter’s server to get new tweets that takes a long time
- Code we want to run using those tweets
**Challenge**: We want to wait for the tweets to be stored in tweets so that they’re there
to run displayTweets on - but no code can run in the meantime

```javascript
//Slow function blocks further code running
const tweets = getTweets("http://twitter.com/will/1")
// ⛔350ms wait while a request is sent to Twitter HQ
displayTweets(tweets)
// more code to run
console.log("I want to runnnn!")

//What if we try to delay a function directly using setTimeout?
//setTimeout is a built in function - its first argument is the function to delay followed by ms to delay by
function printHello(){
 console.log("Hello");
}
setTimeout(printHello,1000);
console.log("Me first!");

//So what about a delay of 0ms
function printHello(){
 console.log("Hello");
}
setTimeout(printHello,0);
console.log("Me first!");
```

**JavaScript is not enough - We need new pieces (some of
which aren’t JavaScript at all)**      
Our core JavaScript engine has 3 main parts:
- Thread of execution
- Memory/variable environment
- Call stack
We need to add some new components:
- Web Browser APIs/Node background APIs
- Promises
- Event loop, Callback/Task queue and micro task queue

```javascript
//ES5 solution: Introducing ‘callback functions’, and Web Browser APIs
function printHello(){ console.log("Hello"); }
setTimeout(printHello,1000);
console.log("Me first!");

//We’re interacting with a world outside of JavaScript now - so we need rules
function printHello(){ console.log("Hello"); }
function blockFor1Sec(){ //blocks in the JavaScript thread for
1 sec }
setTimeout(printHello,0);
blockFor1Sec()
console.log("Me first!");
```
#### ES5 Web Browser APIs with callback functions
**Problems**
- Our response data is only available in the callback function - Callback hell
- Maybe it feels a little odd to think of passing a function into another function only for it
to run much later        
**Benefits**
- Super explicit once you understand how it works under-the-hood

## Coding Problems: 

### Question 1:
Write a closure named createCounter that takes an initial value start and returns a function. The returned function, when invoked,  
should increment the counter by 1 and return the updated value.

#### My Solution

```javascript
function createCounter(start) {
  let counter = start;

  // The returned function increments the counter and returns the updated value
  return function() {
    return counter++;
  };
}

// Create a counter starting from 5
const counter = createCounter(5);

// Each time the counter function is invoked, it will increment the counter by 1
console.log(counter()); // Output: 5
console.log(counter()); // Output: 6
console.log(counter()); // Output: 7
```

### Question 2:
Write a closure named calculateAverage that takes an array of numbers, nums, and returns a function. The returned function, when invoked, should calculate and return the average of the numbers in the array.

#### My Solution
```javascript
function calculateAverage(nums) {
  // Calculate the sum of the numbers in the array
  const sum = nums.reduce((acc, num) => acc + num, 0);

  // The returned function calculates and returns the average
  return function() {
    return sum / nums.length;
  };
}

// Example array of numbers
const numbers = [10, 20, 30, 40, 50];

// Create an average calculator for the array of numbers
const averageCalculator = calculateAverage(numbers);

// Invoke the returned function to calculate and get the average
console.log(averageCalculator()); // Output: 30

```

### Question 3:
Write a closure named powerOf that takes a base number base and returns a function. The returned function, when invoked with an exponent exp, should calculate and return the result of base raised to the power of exp.

#### My Solution
```javascript
function powerOf(base) {
  // The returned function calculates and returns the result of base raised to the power of exp
  return function(exp) {
    return Math.pow(base, exp);
  };
}

// Create a power calculator for base 2
const powerOfTwo = powerOf(2);

// Calculate 2^3 using the power calculator
console.log(powerOfTwo(3)); // Output: 8

// Calculate 2^5 using the power calculator
console.log(powerOfTwo(5)); // Output: 32

```

### Question 4:
Write a closure named compose that takes multiple functions as arguments and returns a new function. The returned function should apply the provided functions in reverse order, passing the result of each function as an argument to the next function.

#### My Solution
```javascript
function compose(...functions) {
  // The returned function applies the provided functions in reverse order
  return function(arg) {
    // Start with the initial argument
    let result = arg;

    // Apply functions in reverse order
    for (let i = functions.length - 1; i >= 0; i--) {
      result = functions[i](result);
    }

    return result;
  };
}

// Example functions
function addTwo(x) {
  return x + 2;
}

function multiplyByThree(x) {
  return x * 3;
}

function subtractTen(x) {
  return x - 10;
}

// Create a composed function
const composedFunction = compose(subtractTen, multiplyByThree, addTwo);

// Use the composed function
console.log(composedFunction(5)); // Output: ((5 + 2) * 3) - 10 = 11

```






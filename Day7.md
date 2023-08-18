# Day 7: Functions & Callbacks
This README file summarizes the JavaScript lesson on Functions & Callbacks.

## Lesson Summary
In this lesson, we explored Functions & Callbacks in JavaScript. Here are the key points covered:
- Java Script Principles.
- Thread of execution, functions, call stack.
- Generalized function, Repeating Functionality, call backes & higher-order functions.
- Arrow Functions.
- Pair Programming.

### JavaScript principles
When JavaScript code runs, it:   
- Goes through the code
line-by-line and runs/ ’executes’
each line - known as the **thread
of execution**
- Saves ‘data’ like strings and
arrays so we can use that data
later - in its **memory**           
We can even save code
(‘functions’)


```javascript
const num = 3;
function multiplyBy2 (inputNumber){
const result = inputNumber*2;
return result;
}
const output = multiplyBy2(num);
const newOutput = multiplyBy2(10);

```

### Functions
Code we save (‘define’) functions &
can use (call/invoke/execute/run)
later with the function’s name & ( )         
**Execution context**          
Created to run the code of a
function - has 2 parts (we’ve
already seen them!)    
- Thread of execution
- Memory

### Call stack
- JavaScript keeps track of what   
function is currently running
(where’s the thread of execution)
- Run a function - add to call stack
- Finish running the function - JS
removes it from call stack
- Whatever is top of the call stack
( that’s the function we’re
currently running)


### Callbacks & Higher Order Functions
- One of the most misunderstood concepts in JavaScript
- Enables powerful pro-level functions like map, filter, reduce (a core aspect of
functional programming)
- Makes our code more declarative and readable
- Forms the backbone of the Codesmith technical interview (and professional
mid/senior level engineering interviews)     

**Why do we even have functions?**           
Create a function 10 squared
- Takes no input
- Returns 10*10

```javascript
//tenSquared
function tenSquared() {
 return 10*10;
}
tenSquared() // 100

//nineSquared
function nineSquared() {
 return 9*9;
}
nineSquared() //81

//What principle are we breaking? DRY (Don’t Repeat Yourself)
```

#### We can generalize the function to make it reusable
```javascript
function squareNum(num){
 return num*num;
}
squareNum(10); // 100
squareNum(9); // 81
squareNum(8); // 64
```

### Generalizing functions
‘Parameters’ (placeholders) mean we don’t need to decide what data to run our
functionality on until we run the function 
- Then provide an actual value (‘argument’) when we run the function
Higher order functions follow this same principle.
- We may not want to decide exactly what some of our functionality is until we
run our function

### Repeating Functionality
```javascript
//Now suppose we have a function copyArrayAndMultiplyBy2
function copyArrayAndMultiplyBy2(array) {
 const output = [];
 for (let i = 0; i < array.length; i++) {
 output.push(array[i] * 2);
 }
 return output;
 }
const myArray = [1,2,3];
const result = copyArrayAndMultiplyBy2(myArray);

//What if want to copy array and divide by 2?
function copyArrayAndDivideBy2(array) {
 const output = [];
 for (let i = 0; i < array.length; i++) {
 output.push(array[i] / 2);
 }
 return output;
 }
const myArray = [1,2,3];
const result = copyArrayAndDivideBy2(myArray);

//Or add 3?
function copyArrayAndAdd3(array) {
 const output = [];
 for (let i = 0; i < array.length; i++) {
 output.push(array[i] + 3);
 }
 return output;
 }
const myArray = [1,2,3];
const result = copyArrayAndAdd3(myArray);

//What principle are we breaking?  DRY - Don’t Repeat Yourself

//We could generalize our function - So we pass in our specific
//instruction only when we run copyArrayAndManipulate !
function copyArrayAndManipulate(array, instructions) {
 const output = [];
 for (let i = 0; i < array.length; i++) {
 output.push(instructions(array[i]));
 }
 return output;
}
function multiplyBy2(input) { return input * 2; }
const result = copyArrayAndManipulate([1, 2, 3], multiplyBy2);

//The outer function that takes in a function is our higher-order function
//The function we insert is our callback function
```

**Functions in javascript = first-class objects**      
They can co-exist with and can be treated like any other javascript object
- Assigned to variables and properties of other objects
- Passed as arguments into functions
- Returned as values from functions


#### Higher-order functions
Takes in a function or passes out a function       
Just a term to describe these functions - any function that does it we call that - but
there's nothing different about them inherently    

#### Callbacks and Higher Order Functions simplify our code and keep it DRY
- **Declarative readable code**: Map, filter, reduce - the most readable way to write
code to work with data
- **Codesmith & pro interview prep**: One of the most popular topics to test in
interview both for Codesmith and mid/senior level job interviews
- **Asynchronous JavaScript**: Callbacks are a core aspect of async JavaScript, and are
under-the-hood of promises, async/await

### Arrow Functions:
```javascript
//Introducing arrow functions - a shorthand way to save functions

const multiplyBy2 = (input) => input*2
const multiplyBy2 = input => input*2
const multiplyBy2 = (input) => { return input*2 }

function multiplyBy2(input) { return input * 2; }
const output = multiplyBy2(3) //6


//Updating our callback function as an arrow function
function copyArrayAndManipulate(array, instructions) {
 const output = [];
 for (let i = 0; i < array.length; i++) {
 output.push(instructions(array[i]));
 }
 return output;
}
const multiplyBy2 = input => input*2
const result = copyArrayAndManipulate([1, 2, 3], multiplyBy2);

//We can even pass in multiplyBy2 directly without a name
//But it’s still just the code of a function being passed into copyArrayAndManipulate
function copyArrayAndManipulate(array, instructions) {
 const output = [];
 for (let i = 0; i < array.length; i++) {
 output.push(instructions(array[i]));
 }
 return output;
}
//const multiplyBy2 = input => input*2  we can pass it directly as below
const result = copyArrayAndManipulate([1, 2, 3], input => input*2);

```

#### Anonymous and arrow functions
- Improve immediate legibility of the code
- But at least for our purposes here they are ‘syntactic sugar’ - we’ll see their
full effects later
- Understanding how they’re working under-the-hood is vital to avoid
confusion


### Pair programming
The most effective way to grow as a software engineer
- Tackle blocks with a partner
- Stay focused on the problem
- Refine technical communication
- Collaborate to solve problem

## Coding Problems: 
### [Use Higher-Order Functions map, filter, or reduce to Solve a Complex Problem](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-higher-order-functions-map-filter-or-reduce-to-solve-a-complex-problem)

#### My Solution
```javascript
const squareList = arr => {
  // Use filter to keep only positive integers
  const positiveIntegers = arr.filter(num => Number.isInteger(num) && num > 0);
  
  // Use map to square the positive integers
  const squaredIntegers = positiveIntegers.map(num => num * num);
  
  // Use reduce to combine the squared integers
  const result = squaredIntegers.reduce((acc, num) => {
    acc.push(num);
    return acc;
  }, []);
  
  return result;
};

const squaredIntegers = squareList([-3, 4.8, 5, 3, -3.2]);
console.log(squaredIntegers);

```

### [Apply Functional Programming to Convert Strings to URL Slugs](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/apply-functional-programming-to-convert-strings-to-url-slugs)

#### My Solution
```javascript
function urlSlug(title) {
  return title
    .split(' ')           // Split the title into an array of words
    .filter(word => word !== '')  // Remove any empty strings from the array
    .map(word => word.toLowerCase())  // Convert each word to lowercase
    .join('-');           // Join the words with hyphens and create the URL slug
}

const slug = urlSlug("A Mind Needs Books Like A Sword Needs A Whetstone");
console.log(slug);  // Output: "a-mind-needs-books-like-a-sword-needs-a-whetstone"

```

### Question 1: Functions and Callbacks
Implement a JavaScript function called mapAsync that takes an array and a callback function. The function should map each element of the array to a new value using the callback function asynchronously.     

The final result should be returned as a Promise.

#### My Solution
```javascript
async function mapAsync(array, callback) {
  const mappedArray = [];
  
  for (const item of array) {
    const result = await callback(item);
    mappedArray.push(result);
  }
  
  return mappedArray;
}

// Example usage
const inputArray = [1, 2, 3, 4, 5];
const asyncMapFunction = async num => {
  return num * 2;
};

mapAsync(inputArray, asyncMapFunction)
  .then(result => {
    console.log(result); // Output: [2, 4, 6, 8, 10]
  })
  .catch(error => {
    console.error(error);
  });


```

### Question 2: Call Stack and Recursion
Write a JavaScript function called sumRange that calculates the sum of all integers in a given range. The function should use recursion to handle the calculation and demonstrate understanding of the call stack.

#### My Solution
```javascript
function sumRange(start, end) {
  if (start === end) {
    return start; // Base case: when start and end are the same, return that value
  } else {
    return start + sumRange(start + 1, end); // Recursive case: add start to the sum of the rest of the range
  }
}

// Example usage
const result = sumRange(1, 5); // Calculates 1 + 2 + 3 + 4 + 5
console.log(result); // Output: 15

```










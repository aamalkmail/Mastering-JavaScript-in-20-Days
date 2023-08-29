# Day 2: Scope , Scope & Function Expression 

This README file summarizes the JavaScript lesson on Scope , Scope & Function Expression.

## Lesson Summary

In this lesson, we explored Scope , Scope & Function Expression in JavaScript. Here are the key points covered:

- Scope , Compilation and scope, code Execution, lexical scope
- Nested Scope.
- Function expression and arrow function.

## scope

### Nested Scope in java script
1- 
Function Scope:
When a function is defined, it creates its own scope. Variables declared inside that function are accessible only within that function, creating a nested scope. If a function is defined within another function, the inner function has access to its own variables and the variables of its parent function.

<img src="![image](https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/7901563e-8b8f-4215-a82d-3267d8c0c9b3)"/>

2-
Block Scope (ES6+):
With the introduction of let and const, block-level scoping became possible. This means that variables declared using let or const are scoped to the nearest enclosing curly braces {}. This allows for nested block scopes within functions or other blocks.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/93a63ac5-9b41-4f81-af82-a7f07a79abb6">

### Compilation:

JavaScript code goes through a quick preparation step before it runs, which includes breaking it down into smaller parts called tokens and organizing these into a tree-like structure.
This structure is then turned into executable code, and the code is executed by the JavaScript engine.

### Scope:

Think of scope as the area where variables live and can be accessed.
Global scope is like the whole house where everyone can access things.
Local scope is like a room within the house, where only things inside that room can be used.
Nested scope means one room is inside another. The inner room can use things from both its own room and the outer room, but the outer room can't use things from the inner room.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/49ae66b1-07fa-4dbe-9eda-f6070cd938cb">

### Hoisting:
What it is: Hoisting moves declarations (not assignments) to the top of their scope during compilation.
Imagine: It's like reading a storybook. You know the main characters' names before you start reading about them in the story.
Example: You can use a variable before you declare it, but only if the declaration is hoisted to the top of the scope.

### Closure:
What it is: A closure is when a function "remembers" its surrounding variables even after the function has finished running.
Imagine: Think of a lunchbox. It keeps your food safe and warm until you're ready to eat, even if you're far from the kitchen.
Example: A function inside another function can still access the variables of the outer function even after the outer function has completed.

### Modules:
What it is: Modules let you organize your code into separate files and use only what you need in each part of your program.
Imagine: Imagine a toolbox with compartments. You only take out the tools you need for a specific task, keeping everything else organized.
Example: Instead of writing all your code in one big file, you can break it into smaller files (modules) for different parts of your application.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/67a1c4fe-51c2-47ca-97ad-5f92a6183e61">

#### In JavaScript, when you have a function inside another function, the inner function creates a nested scope. Variables declared inside the outer function are accessible in both the outer and inner functions. But variables declared inside the inner function are only accessible within that inner function.

## "undefined" and "undeclared" refer to different concepts related to variables.

## 1. Undefined:
What it means: "Undefined" refers to a variable that has been declared but hasn't been assigned a value yet. Example: If you declare a variable x but don't assign any value to it, x is considered "undefined."

## 2. Undeclared:
What it means: "Undeclared" refers to a variable that has been used in code without being formally declared using var, let, or const. Example: If you use a variable y without declaring it first with var, let, or const, y is considered "undeclared."

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/905feae2-b9b0-4093-be91-555d04019067">

## Function Expressions:

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/b01b24cc-a833-4d09-8e56-d5b29d0baca9">

### Function expressions are handy because you can store functions as variables. This makes them easy to pass around, use as arguments in other functions, or even store in objects or arrays.

## Arrow function:

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/e778e288-cc36-48e2-a19a-d6056d9e493c">

arrow functions are like writing cooking instructions using clear and direct sentences to make your code easy to understand and maintain!

************************
# QUESTION 1
Create a function called arrowHOF that takes an arrow function as input and returns a new arrow function that enhances the behavior of the input function.

The enhanced function should accept additional arguments and execute the input function multiple times based on these arguments.

const exampleNormalFunc1 = (a, b, c) => { return a * (b + c); }

const exampleNormalFunc2 = (x, y) => { return x * y; }

const exampleNormalFunc3 = (string) => { return string + " " + string + " " + string + "!"; }

const arrowHOF = (normalFunc) => { // write your code here; }

const hofNormalFunc1 = arrowHOF(exampleNormalFunc1); const hofNormalFunc2 = arrowHOF(exampleNormalFunc2); const hofNormalFunc3 = arrowHOF(exampleNormalFunc3);

console.log(hofNormalFunc1(3, 4, 5)(2)); // logs 60 twice console.log(hofNormalFunc2(20, 35))(4); // logs 700 four times console.log(hofNormalFunc3("Meow")()); // logs "Meow Meow Meow!" once

## SOL:
```
const exampleNormalFunc1 = (a, b, c) => {
  return a * (b + c);
};

const exampleNormalFunc2 = (x, y) => {
  return x * y;
};

const exampleNormalFunc3 = (string) => {
  return string + " " + string + " " + string + "!";
};

const arrowHOF = (normalFunc) => {
  return (...args1) => {
    return (...args2) => {
      const result = normalFunc(...args1);
      return (...multiplier) => {
        const multi = multiplier[0];
        return Array.from({ length: multi }, () => result(...args2));
      };
    };
  };
};

const hofNormalFunc1 = arrowHOF(exampleNormalFunc1);
const hofNormalFunc2 = arrowHOF(exampleNormalFunc2);
const hofNormalFunc3 = arrowHOF(exampleNormalFunc3);

console.log(hofNormalFunc1(3, 4, 5)(2)); // logs 60 twice
console.log(hofNormalFunc2(20, 35)(4)); // logs 700 four times
console.log(hofNormalFunc3("Meow")());  // logs "Meow Meow Meow!" once
```

# QUESTION 2
Build a function called preserveThis that takes a function as input and returns a new arrow function that behaves the same way as the input function but preserves the original this context when used as a method of an object.

// Example object const obj = { name: 'John', greet: function (greeting) { console.log(${greeting}, ${this.name}!); } };

const preserveThis = (func) => { // write your code here; return func; }

// Wrap the greet function using preserveThis const preservedGreet = preserveThis(obj.greet);

// Call the wrapped function as a method of the object preservedGreet('Hello'); // Output: "Hello, John!"

## SOL:

```
const obj = {
  name: 'John',
  greet: function (greeting) {
    console.log(`${greeting}, ${this.name}!`);
  }
};

const preserveThis = (func) => {
  return (...args) => {
    return func.apply(this, args);
  };
}

const preservedGreet = preserveThis(obj.greet);

preservedGreet('Hello'); // Output: "Hello, John!"
```

# QUESTION 3
Consider the 2 following examples and distinguish the different output in each one with them with a reasoning.

Example 1:

function outer1() { var x = 10;

var inner1 = function() { console.log(x); };

inner1(); }

outer1(); // Output: 10 Reasoning for example 1's output:

Example 2:

function outer2() { var x = 10;

var inner2 = function() { var x = 20; console.log(x); };

inner2(); }

outer2(); // Output: 20 Reasoning for example 2's output:



## SOL:
In Example 1, the inner function inner1 accesses the x variable from its parent scope, which is the outer1 function, resulting in an output of 10. In Example 2, the inner function inner2 defines its own x variable with a value of 20, so it logs 20 when executed within the outer2 function.


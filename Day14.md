# Day 14: Advanced Scope

This README file summarizes the JavaScript lesson on Advanced Scope.

## Lesson Summary

In this lesson, we explored Advanced Scope in JavaScript. Here are the key points covered:

- Lexical Scope & Dynamic Scope.
- Function Scoping, Block Scoping.
- Hoisting.


### Lexical Scope:
lexical scope means that the accessibility of a variable is determined by where the variable is declared within the source code. Variables declared in an outer scope are accessible in inner scopes, but variables declared in inner scopes are not accessible in outer scopes.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/ac465ced-ba37-430a-b2c5-0ad3ce45b5da">



### dynamic scope:
Dynamic scope is a different approach to determining variable scope compared to lexical scope. Unlike lexical scope, where scope is determined by the physical structure of the code, dynamic scope focuses on the call hierarchy of functions when determining variable accessibility.


<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/b8d4732a-0b6c-4fa1-8a01-679e16cb085a">

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/61776863-e125-495c-94f4-5e7e3f24d432">


#### IIFE" stands for "Immediately Invoked Function Expression." It's a design pattern in JavaScript that involves creating a function and immediately invoking it. This pattern is often used to create a private scope for variables and avoid polluting the global scope with unnecessary variables.



#### Block scope is a concept in programming that defines the scope of variables based on blocks of code, typically enclosed within curly braces {}. Block scope is used in languages like JavaScript to limit the visibility of variables to specific blocks of code, such as loops or conditional statements.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/362c5a7c-49c5-40c2-bc32-d2710c91b79c">

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/19a0496d-80ad-4972-a582-ca00668e905f">



#### Choosing between let and var in JavaScript:
###### let and Block Scope:

1-Use let when you want to declare variables with block scope.
2-Variables declared with let are limited to the block (curly braces) in which they are defined.
3-They are not accessible outside of the block they're declared in.
4-This helps prevent variable leaks and conflicts in nested blocks, loops, and conditional statements.
5-Preferred choice for modern JavaScript code.
ex:

```
if (true) {
  let x = 10;  // x is only accessible within this block
}
console.log(x);  // This will result in an error because x is not accessible here


```
#### var and Function Scope:

1-Use var when you want to declare variables with function scope.
2-Variables declared with var are accessible within the function in which they are defined.
3-They can also be accessed outside the function if they are defined outside any block.
4-However, var variables are not limited to the block they're declared in, which can lead to unexpected behavior.
5-Considered somewhat outdated due to the issues it can introduce.
ex:
```
function example() {
  if (true) {
    var y = 20;  // y is accessible within the function
  }
  console.log(y);  // y can be used here, even though it's defined inside an if block
}
example();
console.log(y);  // This will result in an error if y is declared inside the function; otherwise, it will log the value

```

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/6f3b8bd8-baff-4a03-a16c-e5a60edd4fec">



## const:

1-Immutable Value: Once a const variable is assigned a value, that value cannot be changed.
2-Block Scope: const variables are block-scoped, just like variables declared with let.
3-Declaration and Initialization: You must assign a value to a const variable when you declare it.
4-Data Types: You can use const to declare constants for any data type, including numbers, strings, objects, arrays, and more.
5-Reference Types: If a const variable holds a reference to an object or array, the contents of the object or array can still be modified. However, the variable itself cannot be reassigned to a new reference.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/7b610e00-c86a-4e06-ab6a-440c90f300fa">



## Hoisting in JavaScript:
##### Hoisting is a behavior in JavaScript where variable and function declarations are moved to the top of their containing scope during the compilation phase, before the code is executed. This means that you can use variables and call functions before they are actually declared in the code. However, it's important to understand that only the declarations are hoisted, not the initializations.


<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/f5ea623b-70aa-46de-8002-4f1c8f42ea9d">

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/0f1f9297-a715-4817-bd31-ba96393075fb">


When you declare a variable with let, its scope is limited to the block where it's defined. Additionally, the variable is not accessible before the point where it's declared in the code. This behavior is sometimes referred to as the "temporal dead zone.

*****************************************************************


## QUESTION #1
Given the following code snippet and explain what's happening.
```
for (var i = 0; i < 5; i++) {
    setTimeout(function() {
      console.log("value of [i] is: ", i);
    }, 100);
}
```
The current output is: "value of [i] is: 5" five times.

The output should be:

"value of [i] is: ", 0 "value of [i] is: ", 1 "value of [i] is: ", 2 "value of [i] is: ", 3 "value of [i] is: ", 4

Without changing anything in the for loop's code itself, provide a solution to fix it.

## SOL:
```
for (let i = 0; i < 5; i++) {
    setTimeout(function() {
        console.log("value of [i] is: ", i);
    }, 100);
}


```


## QUESTION #2
Given the following code snippet and explain what's happening.
```
for (let i = 0; i < 5; i++) {
   let array = [];
   array.push(i);
   console.log("Current array is: ", array)
}
```
The current output is:

"Current array is: [ 0 ]" "Current array is: [ 1 ]" "Current array is: [ 2 ]" "Current array is: [ 3 ]" "Current array is: [ 4 ]".

The output should be: "Current array is: [0, 1, 2, 3, 4]".

Provide a solution to fix it.




## SOL:
```
let array = [];  

for (let i = 0; i < 5; i++) {
   array.push(i); 
   console.log("Current array is: ", array);
}

```



## QUESTION #3
Given the following code snippet and explain what's happening.

let functions = [];

for (var i = 0; i < 5; i++) {
  functions.push(() => {
    console.log("Current value of i is:", i);
  });
}

functions.forEach((func) => func());
The current output is:

"Current value of i is: 5" "Current value of i is: 5" "Current value of i is: 5" "Current value of i is: 5" "Current value of i is: 5"

The output should be:

"Current value of i is: 0" "Current value of i is: 1" "Current value of i is: 2" "Current value of i is: 3" "Current value of i is: 4"

Provide a solution to fix it.


## SOL:
```
let functions = [];

for (let i = 0; i < 5; i++) {
  functions.push(() => {
    console.log("Current value of i is:", i);
  });
}

functions.forEach((func) => func());


```

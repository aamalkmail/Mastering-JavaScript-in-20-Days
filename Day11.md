# Day 11: Types & Coercion

This README file summarizes the JavaScript lesson Types & Coercion.

## Lesson Summary

In this lesson, we explored Types & Coercion in JavaScript. Here are the key points covered:

- Primitive Types,typeOf operator, NaN, Negative Zero 
- Type Coercion ,Abstract operations.
- toString, toBoolean, toNumber, Boxing...

## primitive types 
### js has two kind of data: 
####  1-PRIMITIVE (eg : string , number,boolean, undefined,null,)    
#### 2- OBJECT(eg: document,  friend)

*** undefined is: when something hasn't been given a value yet, 

*** null is: when you're purposely saying there's no value there.

 ### .length:  returns the length of a string.
### String 🔻
are made of a sequence of characters`"super".length //4`are in a specific order, each gets a number, starting at 0 called "index".
index => a number given to a position
## In JavaScript, primitive types are the basic data types that represent simple values. There are six primitive types:

Undefined: Represents a variable that is declared but not assigned a value.
Null: Represents the absence of a value intentionally.
Boolean: Represents either true or false.
Number: Represents numeric values, both integers and decimals.
String: Represents sequences of characters, like text.
Symbol: Represents unique and immutable values (introduced in ES6).

## In JavaScript, variables don't have types, values do:
thats mean:the type of data is determined by the value that is stored in a variable, rather than by the variable itself.

## Undefined: Declared, but no value assigned yet.
## Undeclared: Variable used without being declared first.
## Uninitialized: Declared, but not given an initial value.
### NaN stands for "not a number." It's a special value that represents the result of an operation that should produce a number, but for some reason, the result isn't a valid number.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/3bb83c58-f040-4f48-8cab-180674d4c803">

// if you use the typeof operator on NaN, it will return "number"

console.log(typeof NaN); // Outputs: "number"

```
Object.is(value1, value2);
```

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/5c03d3ec-f475-4d3c-8258-9b780f1a2475">

## The Object.is() method in JavaScript is used to check if two values are the same,  it behaves similarly to ===, but it handles these special cases differently. It returns true if the values are the same, including special cases, and false if they are not the same.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/ab22cd49-af8a-4167-bc77-0cd70545dd3d">

##  Math.sign() function in JavaScript is used to figure out whether a number is positive, negative, or zero. It gives you:

1 if the number is positive.
-1 if the number is negative.
0 if the number is zero.

## In JavaScript, ToPrimitive is a way to turn an object into a simple value like a number or a string when needed. This happens automatically in certain situations, like when you use an object in math or combine it with a string. JavaScript first tries to use the object's own methods called valueOf() and toString() to convert it to a simple value. If those methods don't give a simple value, JavaScript does its best to make sense of the object in a simple way.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/180b59ab-67e8-4133-af5c-a624591f3d7e">

-  toString(): If the valueOf method didn't return a primitive value, or if it's not present, JavaScript will try to call the toString method with the appropriate hint. If the return value is primitive, it is used. If neither valueOf nor toString produces a primitive value, JavaScript will throw an error.

   <img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/4454eeb6-388d-482e-b9e6-76a833ddfcaf">
   

-  toBoolean

   <img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/c900ad1f-753e-4ceb-a876-9ca57faa5e66">

   ## boxing
   Boxing is like putting a primitive value (like a number, string, or boolean) into a special wrapper object. This lets you use object-like features with that value, such as calling methods or accessing properties. However, JavaScript often does this automatically when needed, so you don't usually need to do it yourself.

   <img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/142fd09e-8741-4605-a783-d7ab57bfff0a">

   ## All programming languages have type conversions, because it's absolutely necessary

   ******************
   
   <img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/55340169-6c89-47bf-be86-75e2fdb432e2">
   ************************************

   # Q1

   Write a function called convertStringToNumber that converts a string to a number using the unary plus operator.
   ## Solution

    ```
    function convertStringToNumber(input) {
     if (typeof input === "string") {
    const num = +input; 
    if (!isNaN(num)) {
      return num; } }
    return { value: input, type: typeof input };}
    
# Q2
Write a function called checkNaN that takes a single argument and returns true if the argument is NaN and false otherwise.

```
const checkNaN = (value) => {
  return isNaN(value); };
```
# Q3
Write a function called isEmptyValue that checks if a given input is an empty value (undefined, null, or empty string).

```
function isEmptyValue(value) {
  return value === undefined || value === null || value === "";}
```
# Q4
Write a function called compareObjects that takes 2 arguments of type "object" and compares them. If both arguments are equal, return true. If not, return false.
```
function compareObjects(input1, input2) {
  if (typeof input1 !== "object" || typeof input2 !== "object") {
    return [input1, input2];
  }
  const keys1 = Object.keys(input1);
  const keys2 = Object.keys(input2);
  if (keys1.length !== keys2.length) {
    return false;
  }
 for (const key of keys1) {
    if (input1[key] !== input2[key]) {
      return false;
    }
  }
 return true;}
```
# Q5
Write a function called complexCoercion that takes a single argument and checks if its type is primitive, and if so returns a coerced value according to the rules below

```
const complexCoercion = (input) => {
  if (typeof input !== "object" && typeof input !== "function") {
    if (typeof input === "number") {
      return String(input) === "0" ? false : true;
    } else if (typeof input === "string") {
      return input !== "" ? true : false;
    } else if (input === null || input === undefined) {
      return false;
    }
  }
  return input;
};
```

# Day 3: Arrays & Objects

This README file summarizes the JavaScript lesson on Arrays and Objects. Arrays let us keep multiple values together in a single collection &An object is a collection of properties, and a property is an association between a name (or key) and a value.

## Lesson Summary

In this lesson, we explored Arrays & objects in JavaScript. Here are the key points covered:
- Arrays and some of its methods.
- Mutable vs. Immutable data.
- Objects and some of its methods.

### Arrays 
Arrays let us keep multiple values together in a single collection.     

```javascript
// Example of an array
let synonyms = ["plethora", "array", "cornucopia"];

// Like strings, arrays have a length
synonyms.length

// And each value has an index
synonyms[1]
synonyms.indexOf("cornucopia")// output = 2

// Also like strings, we can check if an array contains a certain value
synonyms.includes("plethora")// output: true
synonyms.includes("variety")// output: false

// Unlike strings, we can modify arrays
synonyms[1] = "variety";//synonyms = ["plethora", "variety", "cornucopia"];
let lastItem = synonyms.pop();// lastItem = "cornucopia"   synonyms = ["plethora", "variety"];
synonyms.push("multitude");//synonyms = ["plethora", "variety", "multitude"];

// Arrays can be empty, or hold a single item
let emptyArray = [];
let oneItemArray = ["lonely"];

// Arrays can hold any type of items, or mix and match!
let mixedArray = ["pop", 6, "squish", false, document];

// Array Methods

["c", "a", "d", "b"].sort() //sort of alphabetical order of things in the array

["lions", "tigers", "bears oh my!"].join(" & ")//join values in the array using a string joiner that we pass in

[1, 2, 3].concat([4, 5, 6])//join two deferent arrays to give us one array with all the elements of both arrays
}

```
### Mutable vs. immutable

**"Mutable"** data can be edited (e.g. Arrays)      

**"Immutable"** data always stays the same (e.g. strings & other primitives)     


```javascript
// Arrays
let abcArray = ["a", "b", "c"];
abcArray[1] = "d";
abcArray;//abcArray = ["a", "d", "c"]

// Strings
let abcString = "abc";
abcString[1] = "d";
abcString;//abcString = "abc"

let numbers1 = [1, 2, 3];
let result1 = numbers1.push(4);
numbers1;//numbers1 = [1, 2, 3, 4]

let numbers2 = [1, 2, 3];
let result2 = numbers2.concat([4]);
numbers2;//numbers2 = [1, 2, 3]

}

```

Some actions "mutate" an array (e.g. oldArray.push(newValue)) ...aka change the array in-place     

Other actions do not mutate the original array, but instead create a new copy (e.g. oldArray.concat(otherArray))     

Variables themselves can also be (im)mutable
```javascript
// mutable variable
let letVariable = "original value";
letVariable = "new value";

// immutable variable
const constVariable = "original value";
constVariable = "new Value";//error we can not change its value

//immutable variable with mutable value
const operands = [4, 6];
const sum = operands[0] + operands[1];//10
operands[0] = 5;
const newSum = operands[0] + operands[1];//11

}

```

### Objects

**Objects** collect multiple values together to describe more complex data, Similar to how we can point at different values using variables in our code,

objects let us point at related values using properties in the object.   
```javascript
//Example of object
const js = {
    name: "JavaScript",
    abbreviation: "JS",
    isAwesome: true,
    officialSpec: "ECMAScript",
    birthYear: 1995,
    creator: "Brendan Eich"
};

//Getting property values
js.name //"JavaScript"
js.isAwesome // true

//Using property values
js.name.startsWith("Java")//true

//Setting property values
const indecisive = {
    lunch: "sandwich"
};
indecisive.lunch = "tacos";// edit the value of lunch
indecisive.snack = "chips";// add the property snack

//Properties can point to functions too ,We call function-properties "methods" on objects
const dog = {
    name: "Ein",
    breed: "Corgi",
    speak: function () {
        console.log("woof woof");
    }
}
dog.speak();

//this in a method lets us reference other properties on the object
anjana.speak = function () {
    console.log("Hi my name is", this.name);
}
anjana.speak();

//Nested objects
const menu = {
    lunch: {
        appetizer: "salad",
        main: "spaghetti",
        dessert: "tiramisu"
    },
    dinner: {
        appetizer: "samosa",
        main: "saag paneer",
        dessert: "gulab jamun"
    }
};
const tiramisu = menu.lunch.dessert;

//Objects in Arrays & Objects
const spices = [
    {name: "Emma", nickname: "Baby"},
    {name: "Geri", nickname: "Ginger"},
    {name: "Mel B", nickname: "Scary"},
    {name: "Mel C", nickname: "Sporty"},
    {name: "Victoria", nickname: "Posh"}
];
const spiceGirls = {
    albums: ["Spice", "Spiceworld", "Forever"],
    motto: "Girl Power",
    members: spices
};



//Built in objects

//document
document.title = "Tic Tac Toe";
document.querySelector("h2").append(" and love");

//console
console.log("hello coder!");
console.log(document.querySelector("h1").textContent);
console.warn("something seems iffy");
console.error("oh no, it broke!");
console.clear();

//Math
let randomNumber = Math.random();
const pi = Math.PI;
const five = Math.abs(-5);

//Strings are primitive values (not objects), but JS automatically wraps them in String objects
const hello = "hello";
console.log(hello.length);
const yello = hello.toUpperCase();
}

```

## Coding Problems: 
### [Copy Array Items Using slice()](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-data-structures/copy-array-items-using-slice)

#### My Solution
```javascript
function forecast(arr) {
  // Only change code below this line
  let arr1 = arr.slice(2,4)
  return arr1;
}

// Only change code above this line
console.log(forecast(['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms']));
```

### [Combine Arrays with the Spread Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-data-structures/combine-arrays-with-the-spread-operator)

#### My Solution
```javascript
function spreadOut() {
  let fragment = ['to', 'code'];
  let sentence = ['learning',...fragment,'is','fun']; // Change this line
  return sentence;
}

console.log(spreadOut());
```

### [Profile Lookup](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/profile-lookup)

#### My Solution
```javascript
// Setup
const contacts = [
  {
    firstName: "Akira",
    lastName: "Laine",
    number: "0543236543",
    likes: ["Pizza", "Coding", "Brownie Points"],
  },
  {
    firstName: "Harry",
    lastName: "Potter",
    number: "0994372684",
    likes: ["Hogwarts", "Magic", "Hagrid"],
  },
  {
    firstName: "Sherlock",
    lastName: "Holmes",
    number: "0487345643",
    likes: ["Intriguing Cases", "Violin"],
  },
  {
    firstName: "Kristian",
    lastName: "Vos",
    number: "unknown",
    likes: ["JavaScript", "Gaming", "Foxes"],
  },
];

function lookUpProfile(name, prop) {
  for (let i = 0; i < contacts.length; i++) {
    if (contacts[i].firstName === name) {
      if (contacts[i][prop] !== undefined) {
        return contacts[i][prop];
      } else {
        return "No such property";
      }
    }
  }
  return "No such contact";
}
lookUpProfile("Akira", "likes");
```
### [Write Reusable JavaScript with Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/write-reusable-javascript-with-functions)

#### My Solution
```javascript
function reusableFunction() {
  console.log("Hi World");
}
reusableFunction();
```

### [Understanding Undefined Value returned from a Function](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/understanding-undefined-value-returned-from-a-function)

#### My Solution
```javascript
// Setup
let sum = 0;

function addThree() {
  sum = sum + 3;
}

// Only change code below this line
function addFive(){
  sum = sum + 5;
}

// Only change code above this line

addThree();
addFive();
```

### [Return a Value from a Function with Return](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/return-a-value-from-a-function-with-return)

#### My Solution
```javascript
function timesFive(num){
  return num*5;
}

timesFive(5);
```

# Day 5: Conditionals, Map & filter, and loops.

This README file summarizes the JavaScript lesson on Conditionals, Map & filter, and loops.

## Lesson Summary

In this lesson, we explored Conditionals, Map & filter, and loops in JavaScript. Here are the key points covered:

- If condition and for loop.
- Map and filter methods.
- Spread operator.
- while loop.
- (A)synchronous code(setTimeout).

### Conditionals

**if** statements let us execute code under a certain condition

```javascript
//code in the if block only runs if the (condition) is true
const you = {wannaBeMyLover: true};
if (you.wannaBeMyLover) {
    you.gottaGetWithMyFriends = true;
}

//we can use else to run other code if (condition) is false
if (you.reallyBugMe) {
    console.log("Goodbye");
} else {
    console.log("Hello");
}


if (5 > 4) {
    console.log("greater than");
} else {
    console.log("less than");
} //That code will print greater than.

//We can chain else and if blocks to account for multiple conditions
function compare(x, y) {
    if (x > y) {
        console.log(x, "is greater than", y);
    } else if (x < y) {
        console.log(x, "is less than", y);
    } else {
        console.log(x, "is equal to", y);
    }
}

//The (condition) is usually an expression that evaluates to a boolean
if (forecast === "rain") {
    console.log("bring an umbrella");
}

//If it's given some other value, JS will convert it to a boolean, and decide based on its "truthiness"
if ("nonempty strings are truthy") {
    console.log("this line will run");
}

if (0) {
    console.log("zero is truthy");
} else {
    console.log("zero is falsy");
}//It will print: zero is falsy

//The ! operator negates a boolean (gives its opposite)
let someoneIsAroundYou = false; 
if (!someoneIsAroundYou) {
    console.log("baby I love you");
}

//Sometimes we care about the truthiness of more than one value
if (you.happy && you.knowIt) {
    you.clapHands();
}
```
Logical "and" (&&) requires both values to be truthy

| A       | B        | A&&B  |
| :-----: | :------: | :----:|
| true    |  true    | true  |
| true    |  false   | false |
| false   |  true    | false |
| false   |  false   | false |

Logical "or" (||) requires only one value to be truthy

| A       | B        | A||B  |
| :-----: | :------: | :----:|
| true    |  true    | true  |
| true    |  false   | true  |
| false   |  true    | true  |
| false   |  false   | false |

#### Conditional ternary operator

a "shortcut" operator for writing quick conditionals
```javascript
//it needs 3 values to work:
condition ? valueIfTrue : valueIfFalse;

let mood = forecast === "sunny" ? "happy" : "sad";
//is equivalent to
let mood;
if (forecast === "sunny") {
    mood = "happy";
} else {
    mood = "sad";
}
```

### loops

**Loops** let us run the same chunk of code multiple times   

for loops require us to:
- declare & initialize a loop counter
- give a condition for the loop to keep running
- describe how to change (usually increment) the counter each time

```javascript
//this is called iteration
for (let rep = 0; rep < 10; rep += 1) {
    console.log("now doing rep", rep);
}
console.log("do you even lift bro");

//Example of for loop
for (let count = 0; count <= 100; count += 10) {
    console.log(count);
}

//for ... of loops let us more easily iterate over items in a collection
const numbers = [1,2,3];
for (let i = 0; i < numbers.length; i++) {
    console.log(numbers[i]);
}
for (let n of numbers) {
    console.log(n);
}

//We can use for...of to iterate over characters in a string
for (let char of "ALOHA") {
    console.log(char);
}
//or items in an array
for (let item of ["pop", 6, "squish"]) {
    console.log(typeof item);
}
//because strings & arrays are "iterables"

```

### Map & filter

The **map** & **filter** methods also let us process all the items in an array

```javascript
//map calls a function on each item in an array to create a new array
const spices = [
    {name: "Emma", nickname: "Baby"},
    {name: "Geri", nickname: "Ginger"},
    {name: "Mel B", nickname: "Scary"},
    {name: "Mel C", nickname: "Sporty"},
    {name: "Victoria", nickname: "Posh"}
];
const nicknames = spices.map(s => s.nickname + " Spice");

//String templates are useful too! Make them with backticks and ${}, e.g.
//`string to insert ${variable} into`
s => `${s.nickname} Spice`;
//is equivalent to
s => s.nickname + " Spice"

//filter calls a true/false function on each item
//and creates a new array with only the items where the function returns true
const mels = spices.filter(s => s.name.includes("Mel"));
```

#### Spread (...)

It lets us take all the items in an array and spread them around.

```javascript
//We can use it to put all the items from one array inside another array
const oldBurns = ["square", "wack"];
const newBurns = ["basic", "dusty", "sus"];
const burnBook = [...oldBurns, ...newBurns];
//equivalent to
const burnBook = oldBurns.concat(newBurns);

//We can also use it to pass all the items from an array as arguments to a function or method
const skills = ["HTML", "CSS", "JS"];
const newSkills = ["React", "TypeScript", "Node"]
skills.push(...newSkills);
console.log(...skills);
```

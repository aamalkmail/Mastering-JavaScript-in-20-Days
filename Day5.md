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

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


```

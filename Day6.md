# Day 6: Data Fetching & Promises, Destructuring Data, Async, and Modules

This README file summarizes the JavaScript lessons on Data Fetching & Promises, Destructuring Data, Async, and Modules.

## Lesson Summary

In this lesson, we explored Data Fetching & Promises, Destructuring Data, Async, and Modules in JavaScript. Here are the key points covered:
- API & Fetch.
- Promises, Await & promises.
- Destructuring Objects and arrays
- Async Functions.
- Modules.
- debugging & error handling.

### Fetching data

**URLs** point to resources on the web    
**https://images.dog.ceo/breeds/bluetick/n02088632_924.jpg**   

```javascript
//APIs provide URLs that point at data we care about
//https://dog.ceo/api/breed/hound/list
  {
    "message": [
      "afghan",
      "basset",
      "blood",
      "english",
      "ibizan",
      "plott",
      "walker"
    ],
    "status": "success"
  }

//fetch() lets us use JS to load data from APIs
fetch("https://dog.ceo/api/breed/hound/list")

//It takes time to fetch data from the network
>> fetch("https://dog.ceo/api/breed/hound/list")
Promise { <state>: "pending" }
//So JS writes us an "IOU" for the data value it doesn't have yet
//aka a Promise of a value
```

### Promises

**Promises** can be in 3 possible states: 

- pending: still waiting for the value, hang tight   
- fulfilled (aka "resolved"): finally got the value, all done
- rejected: sorry couldn't get the value, all done
It takes time for Promises to resolve, so they are "**asynchronous**"

JS adds the task to the TODO list and keeps running our program   
But our program needs the data, we want JS to stop and wait for the Promise to resolve    

### await

**await** lets us tell JS to stop and wait for an asynchronous operation to finish

```javascript
//In the case of a Promise, it waits for it to resolve before continuing with our code
let response = await fetch("https://dog.ceo/api/breed/hound/list");
console.log(response);
//The Promise we get from fetch() resolves to a Response object
//It's body contains the data we care about

//Calling the .json() method on the response parses its body as a JSON object
response.json()
//But that gives us another Promise!

//time awaiting the JSON Promise too
let response = await fetch("https://dog.ceo/api/breed/hound/list");
let body = await response.json();
```

### Destructuring

**Destructuring** is a fancy way of declaring multiple variables at once    
By "extracting" values from an object with their property names

```javascript
//Destructuring
let {name, nickname} = spices[0];

//If we only care about some of the properties, we can omit the others
let {nickname} = spices[2];

//We can also destructure Arrays, assigning variables for their items
const [baby, ginger, scary, sporty, posh] = spices;

//We can ignore the values in the array we don't need
const [emma, geri] = spices;
//We can use commas to "skip" values
const [,,melB] = spices;

//We can use ... to collect remaining values
const [babySpice, ...adultSpices] = spices;

//Let's destructure the data we fetched so that we can use it!
let { message } = body;
//We only really care about the message
```
### async functions

wrap all our async fetching & parsing code up into a function

```javascript
//If we try to await something in a regular function...
function fetchResponse(url) {
    const response = await fetch(url);
    return response;
}
//JS doesn't allow it

//We need to make it an async function
async function fetchResponse(url) {
    const response = await fetch(url);
    return response;
}
//This tells JS to expect to await async operations inside the function
```

### Modules

split big codebases across multiple files
```javascript
//It isn't usually possible in JS to use await outside of a function
<script type="module">
    //...
</script>
//JS modules work differently from JS scripts

//One difference is that we can't use await outside of a function in a script
<script>
    await fetch("https://dog.ceo/api/breed/hound/list");
</script>

//Another difference is that modules create their own scope

//import && export

//export lets us expose variables from our module's scope to the outside world
// myModule.js
const veryUsefulFunction = () => "I came from a module";
export { veryUsefulFunction };

//import lets us use an exposed variable from another module
// otherModule.js
import { veryUsefulFunction } from './myModule.js'
veryUsefulFunction();

```

### Debugging

A certainty of coding (especially in JS):Stuff. Will. Go. Wrong!

```javascript
//console.log() (or .warn() or .error()) is one way to understand what's happening when your program runs
function whyIsntThisWorking(input) {
    console.log("Well at least we got this far");
    console.log(input);
    return thingThatDoesntWork(input);
}

//You can also use the browser's debugger to pause JS and inspect what's happening
function whyIsntThisWorking(input) {
    debugger;
    return thingThatDoesntWork(input);
}
//The debugger statement creates a breakpoint where JS will pause and let you look around
```

### Error handling

Once we've discovered where in our program an error is likely, we can do something about it!

```javascript
//Usually errors will cause JS to stop running our code
thisThrowsAnError();
console.log("I'll never get here");

//try lets us "watch out" for potential errors
//its friend catch lets us manage errors when they occur
try {
    thisMightThrowAnError();
} catch (error) {
    console.error("As if! Error:", error); 
    console.log("Whatever, let's press on anyway");
}
console.log("still rollin' with the homies");
```

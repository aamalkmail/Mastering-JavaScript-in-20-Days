# Day 1: Introduction & DOM

This README file summarizes the JavaScript lesson on the DOM and a brief introduction to JavaScript. DOM is a document object model.

## Lesson Summary

In this lesson, we explored DOM in JavaScript & a brief introduction. Here are the key points covered:

- What is JavaScript?
- HTML& CSS& JS
- What is a DOM?
- Finding Elements in a Web Page.
- .length & .textContext.
- Editing the DOM with JS.

### What is JavaScript?

It's a programming language of the web, it helps websites to do stuff and be interactive also it's a dynamic language

### HTML& CSS& JS
**Html** is the noun, is the thing.        
**CSS** is the adjective, the description of the thing.    
**JS** is the verb, the action.    

### DOM

A simple document :
```
<! DOCTYPE html>
  <html lang="eng-US" >
    <head> ... </head>
    <body>
      <header> ... </header>
      <div id="board"> ... </div>
    </body>
</html>
```

### Finding Elements in a Web Page:

**document**:a built-in object in JavaScript that represents the whole document.           
            
  
  ```javascript
// Example 1: find the title of the document:
 document.title

//Example 2:  the body element:     
   document.body

//Example 3: all the elements within the body:     
   document.body.children

//Example 4: the first element with id="board" :  
  document.getElementById("board")
  document.querySelector("#board")

//Example 5: all the h1 elements
  document.getElementByTagName("h1")
  document.querySelectorAll("h1")

//Example 6:  all the elements with class="player"
  document.getElementByClassName("player")
  document.querySelectorAll(".player")

```
### .length & .textContent

  ```javascript
 // Example 1: the number of elements with class="player":    
   document.getElementByClassName("player").length
  document.querySelectorAll(".player").length

  //Example 2:   the text inside the element with id="p1-name":    
    document.getElementById("p1-name").textContent
    document.querySelector("#p1-name").textContent
 ```

### Editing the DOM with JS
 ```javascript
 // Example 1: Change the page Title:    
   document.title = "My Page"

 //Example 2: replace the text of the #p1-name element:    
    document.getElementById("p1-name").textContent = "Sofia"

 //Example 3: add to the end of the element's current text:    
    document.getElementById("p1-name").append(" & friends")
 ```

## Coding Problems: 
### [Compound Assignment With Augmented Multiplication](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/compound-assignment-with-augmented-multiplication)

#### My Solution


```javascript
let a = 5;
let b = 12;
let c = 4.6;

// Only change code below this line
a *=5;
b *=3;
c *=10;

```

### [Concatenating Strings with the Plus Equals Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/concatenating-strings-with-the-plus-equals-operator)

#### My Solution


```javascript
let myStr = "This is the first sentence.";
myStr += " This is the second sentence.";

```

### [Use Bracket Notation to Find the Nth-to-Last Character in a String](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-bracket-notation-to-find-the-nth-to-last-character-in-a-string)

#### My Solution


```javascript
// Setup
const lastName = "Lovelace";

// Only change code below this line
const secondToLastLetterOfLastName = lastName[lastName.length - 2]; // Change this line

```

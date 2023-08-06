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
 find the title of the document:           
  ` document.title `       
 the body element:     
  ` document.body `        
 all the elements within the body:     
  ` document.body.children `       
 the first element with id="board" :  
  ```
  document.getElementById("board")
  document.querySelector("#board")
  ```
 all the h1 elements
  ```
  document.getElementByTagName("h1")
  document.querySelectorAll("h1")
  ```
 all the elements with class="player"
  ```  document.getElementByClassName("player")
  document.querySelectorAll(".player")
  ```

  ### .length & .textContent

   the number of elements with class="player":    
    ```  
     document.getElementByClassName("player").length
     document.querySelectorAll(".player").length
    ```
    
   the text inside the element with id="p1-name":    
   ```
    document.getElementById("p1-name").textContent
    document.querySelector("#p1-name").textContent
  ```

  ### Editing the DOM with JS

  change the page title:         
  `document.title = "My Page" `     
  replace the text of the #p1-name element:           
  ` document.getElementById("p1-name").textContent = "Sofia" `     
  add to the end of the element's current text:      
  ` document.getElementById("p1-name").append(" & friends") `    
    

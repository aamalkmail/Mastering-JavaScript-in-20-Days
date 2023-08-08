# Day 2: Values & Data Types, Operators, Expressions

This README file summarizes the JavaScript lesson on Values & Data Types, Operators, and Expressions.

## Lesson Summary

In this lesson, we explored Values & Data Types, Operators, and Expressions in JavaScript. Here are the key points covered:

- What are the Values & some of the data types in JS?
- Operators and examples of them.
- Expression and the difference between them and statements.

### Values & Data Types:

**Values**: chunks of information we want to work with, that information (data) can be of different types.     

**typeOf**: tells you the type of a value.    

**JS has two kinds of data**:       
**Primitive types** (e.g. strings, numbers)      
**Objects** (e.g. document & friends)      

**undefined** accidental nothing       
**null** deliberate nothing

### Strings
Strings are made of Characters in a specific order, each gets a number, starting at 0

```javascript
// Example 1: How many characters are in this string?
"super".length // Output: 5

// Example 2: What's the first character in the string?
"ALOHA"[0] // Output: A

// Example 3: What's the index of a specific character?
"ALOHA".indexOf("L") // Output: 1

// Example 4: Does this string contain some other string?
"ALOHA".includes("HA") // Output: true

// Example 5: Does this string start with some other string?
"ALOHA".startsWith("AL") // Output: true

// Example 6: At what index does this substring begin?
"ALOHA".indexOf("HA") // Output: 3

// Example 7: Connecting strings together
"ALOHA" + "!" // Output: ALOHA!
}

```

### Operators
- Arithmetic operators     
+ add     
- subtract     
* multiply     
/ divide

Order of operations     
4 + 1 * 2 * 4 + 2   same as in math, use () to group    

((4 + 1) * 2 * 4) + 2     


- Comparison operators   
> greater than       
< less than      
>= greater than or equal to      
<= less than or equal to

- 1 === "1"	vs.	1 == "1" 
"1 === '1'" is a strict equality comparison, checking both value and data type. It evaluates to false because the data types are different (number vs. string). On the other hand, "1 == '1'" is a loose equality comparison that coerces types if needed. It evaluates to true as the values are the same after type coercion.

### Expressions:

Expressions: evaluates (aka resolves) to a value (ex. 4 / 2 * 10)     

- Statements vs. Expressions
  An *expression* "asks" JS for a value.
  A *statement* "tells" JS to do something(e.g. declare/assign a variable).
  
### Variables
  
 **Variables** Let us remember values           

 ```javascript
// Example 1: Declaring a variable
let bankruptcy;

// Example 2: Assigning a variable
let myDeclaredVariable;
myDeclaredVariable = "so value, much wow";

// Example 3: Declaring & assigning at once
let myAssignedVariable = "such efficient, amaze";

//Example 4: Declaring & assigning forever
//const declares & assigns a "constant"
//aka a variable that can't be changed
const myUnchangeableVariable = "Never gonna give you up";

}

```

## Coding Exercises

#### QUESTION #1

Consider the following JavaScript code:

```javascript
let a = 0;
let b = "0";
let c = false;
let d = "false";

console.log(a == b);// output = true
console.log(b === c);// output = false
console.log(!!d);// output = true
```

What will be the output of each console.log statement? **_You MUST explain WHY_**.   
- The == operator in JavaScript performs type coercion, which means it converts operands to the same type before comparison
- The === operator is a strict equality operator that checks both value and type.
- The !! is a double negation operator that is used to convert a value to its boolean equivalent. In JavaScript, any non-empty string is considered truthy. Since the string "false" is non-empty, applying the double negation will result in a boolean true

-------------------------------------------------------------------

#### QUESTION #2:


Consider the following JavaScript expression:

```javascript
console.log(4 + 5 * "7");// output = 39
```

What will be the output of this expression? **_You MUST explain the steps of evaluation taken by JS_**.                
- First we calculate the multiplication because it  has a higher precedence than the addition 5 * "7" = 5 * 7 (since "7" is coerced into the number 7) = 35
- Then we perform the addition 4 + 35 = 39
-------------------------------------------------------------------

#### QUESTION #3:

Evaluate the following expression:

```javascript
let result = 5 + 2 * 3 - 1;// output = 10
```

What will be the output of this expression? **_You MUST explain the steps of evaluation taken by JS_**.
- First we calculate the multiplication because it has a higher precedence than addition and subtraction operators 2 * 3 = 6
- Then the addition 5 + 6 = 11
- Finally the subtraction is performed 11 - 1 = 10
-------------------------------------------------------------------

#### QUESTION #4:

Consider the following code:

```javascript
let x = 10;
let y = '10';
console.log(x == y);// output = true
console.log(x === y);// output = false
```
What will be the output of each `console.log` statement? **_You MUST explain WHY_**.
- The == operator in JavaScript performs type coercion, which means it converts operands to the same type before comparison
- The === operator is a strict equality operator that checks both value and type.
-------------------------------------------------------------------

#### QUESTION #5:

Given the code below:

```javascript
let num = "15";
let isPositive = true;
let result = (num > 10 && isPositive) || num < 0;
console.log(result);// output = true
```

What is the value of result? **_You MUST explain the steps of evaluation taken by JS_**

- num > 10 will be evaluated as **true** because the string "15" is coerced into a number, and 15 is  greater than 10.     
- isPositive is **true**.    
- the result of this part is **true** && **true**, which is **true**         
- num < 0:  15 is not less than 0.So, the result of this part is **false**    
- => (true) || (false):Since one of the conditions (true) is true, the overall result of the expression is ***true***.



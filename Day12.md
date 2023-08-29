# Day 12: Philosophy of Coercion, Equality , and Static Typing

This README file summarizes the JavaScript lesson on Philosophy of Coercion, Equality , and Static Typing.

## Lesson Summary

In this lesson, we explored Philosophy of Coercion, Equality , and Static Typing in JavaScript. Here are the key points covered:

- Intentioal Coercion, Implicit Coercion.
- Double & trible equal and corner cases of them.
- Type Script, pros & Cons of static typing.

## You don't deal with these type conversion corner cases by avoiding coercions.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/bd12df02-6d53-4c22-be4b-dc8ef387f3ff">

means that the dynamic typing feature in JavaScript is not a drawback or weakness; instead, it is considered one of the language's strong and valuable features.
## implicit
In JavaScript, "implicit" refers to actions or behaviors that happen automatically without the need for explicit instructions. For example, when you declare a variable without using the var, let, or const keyword, JavaScript will treat it as an implicit global variable. Similarly, implicit type conversion occurs when JavaScript automatically converts one data type to another without you explicitly instructing it to do so.

These implicit actions can be convenient, but they can also lead to unexpected behavior if not understood and used carefully.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/bb81190c-86ba-4f74-9082-f930df1fc6b9">

*******************

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/6e4bc04c-9484-4321-b7ec-824836d93373">

##  In JavaScript, the double equals (==) is used for loose equality comparison, which means it checks whether the values on both sides are equal after performing type coercion (automatic type conversion). On the other hand, the triple equals (===) is used for strict equality comparison, where it not only checks if the values are equal but also ensures that their types are the same, without performing type coercion. Using === is generally considered safer and more predictable for comparing values in JavaScript.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/c0a80387-757f-4177-9825-710095ce1b5c">

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/9f1649e9-f767-4d9c-bf3b-de2a90f64e52">

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/47d766e5-06ce-41df-9fab-e9b859e8cf72">

###  JavaScript uses strict equality (===) to check if values are of the same type and have the same value. When comparing different types or non-primitive values, JavaScript applies certain conversion rules to make the comparison possible. The "Prefer ToNumber" behavior is applied when comparing a non-primitive with a primitive, and JavaScript tries to convert one of the operands to a number if the other operand is a number.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/4f3dc6be-3c80-4921-912d-beed50a38f69">

********************

## simple rules to work effectively with boolean values in JavaScript!

1-True and False: In JavaScript, you have true and false as the basic boolean values.

2-Truthy and Falsy: Some values are treated as true or false in conditions. Empty things like 0, "", null, undefined, and NaN are treated as false. Everything else is treated as true.

3-Negation (!): Putting a ! in front of a value flips its truthiness. !true becomes false, and !false becomes true.

4-Double Negation (!!): Using !! converts a value to its boolean equivalent. !!0 becomes false, and !!"hello" becomes true.

5-Logical AND (&&): true && false is false. If the first value is false, the result is always false.

6-Logical OR (||): true || false is true. If the first value is true, the result is always true.

7-Comparisons: When you compare things, like 5 > 3, you get a boolean result (true in this case).

## TypeScript and Flow are tools that enhance JavaScript by adding type checking, which improves code quality and reduces bugs. Type-aware linting extends the benefits of linting by incorporating type-related checks into the linting process. This combination helps you catch more issues early in the development process and create more reliable and maintainable code.

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/dbda5ac9-e55e-44c0-a4cf-22157bbdb346">

<img src="https://github.com/mahaalqerem/Mastering-JavaScript-in-20-Days/assets/138065974/cb6cf271-bec4-4273-bd80-2da9ca97094c">

***************************

# Q1:
Given the following promisesArray, convert the array into an object using the convertToObj function.

You should apply typescript types to every promise, the input of convertToObj, and the output of convertToObj.

Build interfaces and types as needed.
## solution:

```
interface HelloWorldResponse {
  message: string;
}

interface CheckBooleanResponse {
  result: boolean;
}

interface ReturnObjResponse {
  x: string;
  y: number;
}

const sayHelloWorld = new Promise<HelloWorldResponse>((resolve, reject) => {
  resolve({ message: "Hello world!" });
});

const checkBoolean = (boolean: boolean) => new Promise<CheckBooleanResponse>((resolve, reject) => {
  if (boolean) {
    resolve({ result: boolean });
  } else {
    reject(`Input is false :(`);
  }
});

const returnObj = new Promise<ReturnObjResponse>((resolve, reject) => {
  resolve({
    x: "meow",
    y: 45,
  });
});

const promisesArray = [sayHelloWorld, checkBoolean(true), returnObj];

const convertToObj = async (array: Promise<any>[]) => {
  const obj: Record<string, any> = {};

  await Promise.all(array.map(async (promise, index) => {
    try {
      const result = await promise;
      obj[`promise${index + 1}`] = result;
    } catch (error) {
      obj[`promise${index + 1}`] = { error: error.message };
    }
  }));

  return obj;
};

(async () => {
  const resultObj = await convertToObj(promisesArray);
  console.log(resultObj);
})();
```

# Q2
What will be the output of the following code snippet? Pick the right choice then justify your answer with an explanation.
```
function testScope1() {
  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;
  }
  console.log(a);
  console.log(b);
  console.log(c);
}

testScope1();
```
Choices:

A) undefined, undefined, undefined
B) 1, undefined, ReferenceError
C) 1, ReferenceError, ReferenceError
D) 1, ReferenceError


# Solution:
C) 1, ReferenceError

# Q3
What will be the output of the following code snippet? Pick the right choice then justify your answer with an explanation.
```
function testScope2() {
  console.log(a);
  console.log(b);
  console.log(c);
  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;
  }
}

testScope2();
```
Choices:

A) undefined, ReferenceError
B) 1, undefined, ReferenceError
C)undefined, undefined, ReferenceError
D) 1, ReferenceError

## The correct choice is:

A) undefined, ReferenceError

# Q4:
What will be the output of the following code snippet? Pick the right choice then justify your answer with an explanation.
```
function testScope3() {
  var a = 36;
  let b = 100;
  const c = 45;

  console.log([a, b, c]);

  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;

    console.log([a, b, c]);
  }

  console.log([a, b, c]);
}

testScope3();
```
choices:

A) [ 36, 100, 45 ] | [ 1, 2, 3 ] | [ 36, 2, 3 ]
B) [ 36, 100, 45 ] | [1, 2, 3 ] | [ 36, 100, 45 ]
C) [ 36, 100, 45 ] | [ 1, 2, 3 ] | [ 1,100, 45 ]
D) [ 36, 100, 45 ] | [ 1, 2, 3 ] | [ 1, 2, 3 ]

## The correct choice is:

A) [36, 100, 45] | [1, 2, 3] | [1, 100, 45]

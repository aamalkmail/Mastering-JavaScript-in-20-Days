# Day 9: Promises

This README file summarizes the JavaScript lesson on Promises.A Promise in JavaScript is an object that represents a value which might be available now, or in the future, or never. It's used for handling asynchronous operations such as fetching data from a server, reading files, or any other tasks that might take some time to complete.

## Lesson Summary
In this lesson, we explored Promises in JavaScript. Here are the key points covered:
- Promises and Examples on them
- Callback Queue & Event loop
- Fetch & then
- Microtask Queue
  
### Promises
Using two-pronged ‘facade’ functions that both:
- Initiate background web browser work and
- Return a placeholder object (promise) immediately in JavaScript

```javascript
//ES6+ Promises
function display(data){
 console.log(data)
}
const futureData = fetch('https://twitter.com/will/tweets/1')
futureData.then(display);

console.log("Me first!");
```

#### ES6+ Solution (Promises)
Special objects built into JavaScript that get returned immediately when we make
a call to a web browser API/feature (e.g. fetch) that’s set up to return promises
(not all are)        
Promises act as a placeholder for the data we expect to get back from the web
browser feature’s background work     

#### then method and functionality to call on completion
Any code we want to run on the returned data must also be saved on the promise
object      
Added using .then method to the hidden property ‘onFulfilment’
Promise objects will automatically trigger the attached function to run (with its
input being the returned data       

```javascript
//But we need to know how our promise-deferred functionality gets back into JavaScript to be run
function display(data){console.log(data)}
function printHello(){console.log("Hello");}
function blockFor300ms(){/* blocks js thread for 300ms }
setTimeout(printHello, 0);
const futureData = fetch('https://twitter.com/will/tweets/1')
futureData.then(display)
blockFor300ms()
console.log("Me first!");
```

#### Promises
**Problems**
- 99% of developers have no idea how they’re working under the hood
- Debugging becomes super-hard as a result
- Developers fail technical interviews        
**Benefits**
- Cleaner readable style with pseudo-synchronous style code
- Nice error handling process

#### We have rules for the execution of our asynchronously delayed code

Hold promise-deferred functions in a microtask queue and callback function in a
task queue (Callback queue) when the Web Browser Feature (API) finishes
Add the function to the Call stack (i.e. run the function) when:
- Call stack is empty & all global code run (Have the Event Loop check this
condition)
Prioritize functions in the microtask queue over the Callback queue

#### Promises, Web APIs, the Callback & Microtask Queues and Event loop enable:

**Non-blocking applications**: This means we don’t have to wait in the single thread
and don’t block further code from running
**However long it takes**: We cannot predict when our Browser feature’s work will
finish so we let JS handle automatically running the function on its completion
**Web applications**: Asynchronous JavaScript is the backbone of the modern web -
letting us build fast ‘non-blocking’ applications   

## Coding Problems:

### Question 1:
You are given a function `executeInSequenceWithCBs` and some code. The task is to modify the `executeInSequenceWithCBs` function so that it runs and executes all the tasks inside the asyncTasks array.

The function should return an array of messages obtained from each task's execution.

You are only allowed to change the `executeInSequenceWithCBs` function or add new functions/code. You cannot modify the tasks' functions.
```javascript

const task1 = (cb) => setTimeout(() => {
  const message = "Task 1 has executed successfully!";
  cb(message);
}, 3000)

const task2 = (cb) => setTimeout(() => {
  const message = "Task 2 has executed successfully!";
  cb(message);
}, 0)

const task3 = (cb) => setTimeout(() => {
  const message = "Task 3 has executed successfully!";
  cb(message);
}, 1000)

const task4 = (cb) => setTimeout(() => {
  const message = "Task 4 has executed successfully!";
  cb(message);
}, 2000)

const task5 = (cb) => setTimeout(() => {
  const message = "Task 5 has executed successfully!";
  cb(message);
}, 4000)

const asyncTasks = [task1, task2, task3, task4, task5];

const executeInSequenceWithCBs = (tasks, callback) => {}

```

#### My Solution
```javascript
const executeInSequenceWithCBs = (tasks, callback) => {
  const results = [];
  let currentIndex = 0;

  const executeNextTask = () => {
    if (currentIndex < tasks.length) {
      const currentTask = tasks[currentIndex];
      currentTask(message => {
        results.push(message);
        currentIndex++;
        executeNextTask();
      });
    } else {
      callback(results);
    }
  };

  executeNextTask();
};

const asyncTasks = [task1, task2, task3, task4, task5];

executeInSequenceWithCBs(asyncTasks, messages => {
  console.log(messages);
});

```

### Question 2:
You are given a function called `executeInParallelWithPromises`, which takes an
array of APIs (represented by objects). 

Your task is to write code that fetches the data of each API in parallel using
promises. In Parallel means that the api which resolves first, returns its value
first, regardless of the execution order. 

The output of the `executeInParallelWithPromises` function should be an array
containing the results of each API's execution.

Each result should be an object with three keys: `apiName`, `apiUrl`, and
`apiData`..
```javascript
const apis = [
  {
    apiName: "products", 
    apiUrl: "https://dummyjson.com/products",
  }, 
  {
    apiName: "users", 
    apiUrl: "https://dummyjson.com/users",
  }, 
  {
    apiName: "posts", 
    apiUrl: "https://dummyjson.com/posts",
  }, 
  {
    apiName: "comments", 
    apiUrl: "https://dummyjson.com/comments",
  }
]

const executeInParallelWithPromises = (apis) => {}

```

#### My Solution
```javascript
const axios = require('axios'); 

const executeInParallelWithPromises = async (apis) => {
  const promises = apis.map(api => {
    return axios.get(api.apiUrl)
      .then(response => {
        return {
          apiName: api.apiName,
          apiUrl: api.apiUrl,
          apiData: response.data
        };
      })
      .catch(error => {
        return {
          apiName: api.apiName,
          apiUrl: api.apiUrl,
          error: error.message
        };
      });
  });

  return Promise.all(promises);
};

const apis = [
  {
    apiName: "products",
    apiUrl: "https://dummyjson.com/products",
  },
  {
    apiName: "users",
    apiUrl: "https://dummyjson.com/users",
  },
  {
    apiName: "posts",
    apiUrl: "https://dummyjson.com/posts",
  },
  {
    apiName: "comments",
    apiUrl: "https://dummyjson.com/comments",
  }
];

executeInParallelWithPromises(apis)
  .then(results => {
    console.log(results);
  })
  .catch(error => {
    console.error("Error:", error);
  });

```

### Question 3:
You are given a function called `executeInSequenceWithPromises`, which takes an
array of APIs (represented by objects). 

Your task is to write code that fetches the data of each API sequentially (one
after the other) using promises. 

In Sequence means that the api which executes first, returns its value
first.

The output of the `executeInSequenceWithPromises` function should be an array
containing the results of each API's execution.

Each result should be an object with three keys: `apiName`, `apiUrl`, and
`apiData`.
```javascript

const apis = [
  {
    apiName: "products", 
    apiUrl: "https://dummyjson.com/products",
  }, 
  {
    apiName: "users", 
    apiUrl: "https://dummyjson.com/users",
  }, 
  {
    apiName: "posts", 
    apiUrl: "https://dummyjson.com/posts",
  }, 
  {
    apiName: "comments", 
    apiUrl: "https://dummyjson.com/comments",
  }
]

//modify and write your code here
const executeInSequenceWithPromises = (apis) => {}

```

#### My Solution
```javascript
const axios = require('axios'); 

const executeInSequenceWithPromises = async (apis) => {
  const results = [];

  for (const api of apis) {
    try {
      const response = await axios.get(api.apiUrl);
      results.push({
        apiName: api.apiName,
        apiUrl: api.apiUrl,
        apiData: response.data
      });
    } catch (error) {
      results.push({
        apiName: api.apiName,
        apiUrl: api.apiUrl,
        error: error.message
      });
    }
  }

  return results;
};

const apis = [
  {
    apiName: "products",
    apiUrl: "https://dummyjson.com/products",
  },
  {
    apiName: "users",
    apiUrl: "https://dummyjson.com/users",
  },
  {
    apiName: "posts",
    apiUrl: "https://dummyjson.com/posts",
  },
  {
    apiName: "comments",
    apiUrl: "https://dummyjson.com/comments",
  }
];

executeInSequenceWithPromises(apis)
  .then(results => {
    console.log(results);
  })
  .catch(error => {
    console.error("Error:", error);
  });

```

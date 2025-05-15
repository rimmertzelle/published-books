# JS asynchronous

## Github repo
For the next lesson we are going to work with the following github [repo](https://github.com/HZ-HBO-ICT/my-second-monolith). This is een application within a node environment. If you watch closely, you can see somewhat simalarities compared to a Laravel application.  

Please try to answer the following answers
1. What is routing and where to find it in this example?
2. What does the controller do?
3. Prisma is an external library; what does it do en what does it represent?

## Important topics before we start

Some topics before we dive into asynchronous computing

### Callbacks

When working with asynchronous operations you have to understand callbacks
In JavaScript, a callback is a function that is passed as an argument to another function and is executed after its parent function has completed. Callbacks can be synchronous or asynchronous. Synchronous callbacks are executed at the same time as the higher-order function that uses it, while asynchronous callbacks allow a function to be executed after an asynchronous operation has completed.

For example, in the array method forEach(), the callback function is executed for each element in the array. Here's an example:

```javascript
let numbers = [1, 2, 3, 4, 5];
numbers.forEach(function(number) {
    console.log(number * 2);
});

```
In this example, function(number) { console.log(number * 2); } is the callback function. For each element in the numbers array, it logs the element multiplied by two.

### Higher order function

A higher-order function in JavaScript is a function that either takes one or more functions as arguments or returns a function as its result. The concept of higher-order functions is derived from mathematics and is used in programming for tasks that require abstract operations, such as error handling, filtering, mapping, or reducing a list of values. Examples of higher-order functions in JavaScript include map(), filter(), reduce(), and forEach(), among others.

### Asynchronous computing
Asynchronous computing in JavaScript allows tasks to run in the background while other tasks continue to run concurrently. This means that JavaScript does not have to wait for one task to complete before moving on to the next one. This is particularly important in cases where tasks are time-consuming or dependent on external resources, such as network requests.
The Promise object is one way JavaScript implements asynchronous programming. A Promise represents a value that may not be available yet but will be at some point or might never be.

Here's a simple example of a Promise:

```javascript

let promise = new Promise(function(resolve, reject) {
    setTimeout(function() {
        resolve("Promise fulfilled!");
    }, 5000);
});

promise.then(function(value) {
    console.log(value);
});

```
In this example, a new Promise is created that will resolve with the value "Promise fulfilled!" after 5 seconds. The then method is used to schedule code to be run once the Promise is fulfilled.

### Fetch, async/await and Promises

In JavaScript, fetch, async/await, and Promise are all related to handling asynchronous operations, but they serve different purposes.
A Promise is an object that represents a value that might not be available yet. It provides methods to handle the eventual completion (or failure) of an asynchronous operation and its resulting value. Promises can be chained, and they also have error handling mechanisms.
fetch is a function in JavaScript used to make HTTP requests, like GET or POST requests. The fetch function returns a Promise that resolves to the Response object representing the response to the request. This is why you often see the fetch function used with the .then() method, which is a method of the Promise object.
async/await is a syntax sugar built on top of promises for working with asynchronous code. It makes your asynchronous code look and behave like synchronous code. This makes it easier to read and understand. The async keyword is used to define an asynchronous function, which always returns a promise. The await keyword is used inside an async function to pause the execution of the function until a Promise is resolved or rejected.

Here's an example of how these concepts can be used together:
```javascript
async function getJson(url) {
    let response = await fetch(url);

    if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
    } else {
        let json = await response.json();
        return json;
    }
}

```
In this example, the fetch function is used to make a request to a URL, and it returns a Promise. The await keyword is used to pause the execution of the getJson function until the Promise resolves. Once the Promise resolves, the Response object is converted to JSON using the .json() method, which also returns a Promise. The await keyword is used again to pause the execution of the function until the Promise from the .json() method resolves. Finally, the JSON data is returned by the getJson function.

### Concurrent operation / requests

In cases where multiple operations should be performed concurrently and you want to wait for all of them to complete, you can use Promise.all(). This function returns a promise that fulfils when all of the promises passed as an iterable have been fulfilled, or rejects as soon as one of them rejects.

Here's an example:

```javascript
let promise1 = fetch('<https://api.example.com/data1>').then(response => response.json());
let promise2 = fetch('<https://api.example.com/data2>').then(response => response.json());

Promise.all([promise1, promise2])
    .then(values => {
        console.log('Data1:', values[0]);
        console.log('Data2:', values[1]);
    })
    .catch(error => console.error('Error:', error));

```
In this example, two fetch requests are made concurrently. The Promise.all() function is used to wait for both fetch operations to complete. The results are then logged to the console. Note that the results are an array of the fulfilled values in the same order as the promises passed to the Promise.all() function.
However, Promise.all() fails fast, meaning that if any one of the promises passed to it rejects, Promise.all() immediately rejects with that error. If you want to wait for all promises to fulfill or reject regardless of any individual failure, you can use Promise.allSettled():

```javascript
let promise1 = fetch('<https://api.example.com/data1>').then(response => response.json());
let promise2 = fetch('<https://api.example.com/data2>').then(response => response.json());

Promise.allSettled([promise1, promise2])
    .then(results => {
        results.forEach((result, index) => {
            if (result.status === 'fulfilled') {
                console.log(`Data${index + 1}:`, result.value);
            } else {
                console.error(`Error fetching Data${index + 1}:`, result.reason);
            }
        });
    });

```
In this example, Promise.allSettled() is used instead of Promise.all(). This means that both fetch operations are waited on, regardless of whether they fulfill or reject. The results are then logged to the console.

## Videos that explain some of the concepts

Some videos on relevant topics (great and insightful!)
- [Event Loop](https://www.youtube.com/watch?v=eiC58R16hb8); meaningful to watch:  
- [Promises](https://www.youtube.com/watch?v=Xs1EMmBLpn4): promisses visually explained
- [Closures](https://www.youtube.com/watch?v=6Ixyltr8_R0 ): an advanced js concept you need to understand

## Further reading
- [JavaScript Visualized: Promises & Async/Await](https://dev.to/lydiahallie/javascript-visualized-promises-async-await-5gke)
- [Promises, async/await](https://javascript.info/async)
- [Asynchronous Programming :: Eloquent JavaScript](https://eloquentjavascript.net/11_async.html)
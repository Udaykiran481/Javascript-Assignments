# Assignment-10

### Q-1 Answer  

Asynchronous programming a programming paradigm that allows multiple tasks to be executed concurrently without blocking the execution of the main program. In traditional synchronous programming, each operation is executed sequentially, meaning the program waits for one task to complete before moving on to the next one. Asynchronous programming, on the other hand, enables tasks to run independently in the background, allowing the main program to continue its execution without waiting for the completion of these tasks.

Asynchronous programming is essential for handling time-consuming operations, such as reading from files, making network requests, or performing database queries, without causing the program to become unresponsive and slow. In JavaScript, asynchronous programming is commonly used to deal with tasks that involve waiting for I/O (Input/Output) operations, where the program doesn't have to perform computations actively but needs to wait for the result to be available.

JavaScript provides several mechanisms for handling asynchronous programming:

1. Callbacks: The traditional approach to handle asynchronous tasks in older JavaScript versions. Callback functions are passed as arguments to asynchronous functions, and they are invoked once the task is completed or an error occurs.

2. Promises: Introduced in ECMAScript 6 (ES6), promises are objects that represent the eventual completion (or failure) of an asynchronous operation. Promises provide a more structured and readable way to handle asynchronous code.

3. Async/Await: Also introduced in ECMAScript 6 (ES6), async/await is a syntax built on top of promises, making asynchronous code look more like synchronous code. The `async` keyword is used to define asynchronous functions, and the `await` keyword is used to pause the execution until a promise is resolved.

---

### Q-2 Answer

In JavaScript, callbacks are functions that are passed as arguments to another function and are executed after the completion of that function. They allow you to control the flow of asynchronous operations, such as handling the result of an API call or performing an action after a certain event has occurred.

Callbacks are commonly used in scenarios where a function takes time to complete, like reading a file, making an HTTP request, or executing a time-consuming operation. Instead of waiting for the function to complete before moving on to the next line of code, callbacks allow you to define what should happen once the operation is finished.

Here's a simple example of using a callback in JavaScript:

```javascript
// Function that simulates an asynchronous operation
function fetchData(callback) {
  setTimeout(() => {
    const data = [1, 2, 3, 4, 5];
    callback(data); // Call the callback function with the data as an argument
  }, 2000); // Simulate a delay of 2 seconds
}

// Callback function to handle the fetched data
function processData(data) {
  console.log("Data received:", data);
}

// Call the fetchData function and pass the processData function as a callback
fetchData(processData);

console.log("This log will appear before the fetched data because fetchData is asynchronous.");
```
---

### Q-3 Answer

 A promise is a built-in object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. It is part of the ECMAScript 6 (ES6) specification and provides a more organized and cleaner way to handle asynchronous code.

A promise can be in one of the following three states:

1. Pending: The initial state. The promise is neither fulfilled nor rejected. It is still in progress and waiting for the asynchronous operation to complete.
2. Fulfilled (or Resolved): The promise has successfully completed its operation, and the associated value (result) is available.
3. Rejected: The promise has encountered an error during its operation, and the associated reason for the failure is available.


```javascript
// Example function that returns a promise
function fetchData() {
  return new Promise((resolve, reject) => {
    // Simulate an asynchronous operation (e.g., fetching data from a server)
    setTimeout(() => {
      const data = { exampleData: "This is some data" };
      
      // Simulate a successful response
      // Call 'resolve' to change the promise state to fulfilled
      resolve(data);

      // Simulate an error
      // Call 'reject' to change the promise state to rejected
      // reject(new Error("Something went wrong"));
    }, 2000);
  });
}

// Usage of the promise
fetchData()
  .then((result) => {
    console.log("Fulfilled:", result);
  })
  .catch((error) => {
    console.error("Rejected:", error);
  });
```

----

### Q-4 Answer


```javascript
function delayResolveWithMessage() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Hello JavaScript");
    }, 5000);
  });
}

delayResolveWithMessage()
  .then((message) => {
    console.log("Resolved Message:", message);
    console.log("Length of the string:", message.length);
  })
  .catch((error) => {
    console.error("Error occurred:", error);
  });
```
---
### Q-5 Answer

"Callback hell" is a term used to describe a situation in JavaScript where multiple nested callbacks are used to handle asynchronous operations. This can lead to code that is difficult to read, understand, and maintain. Asynchronous operations are common in JavaScript when dealing with tasks like making API calls, reading files, or performing network operations, and callbacks are one way to handle the results of these asynchronous tasks.

Here's an example of callback hell:

```javascript
asyncOperation1(function (result1) {
  asyncOperation2(result1, function (result2) {
    asyncOperation3(result2, function (result3) {
      // More nested callbacks...
    });
  });
});
```

As you can see, as the number of nested callbacks increases, the code becomes less readable and harder to manage, leading to maintenance issues and potential bugs.

Promises provide a cleaner and more structured approach to handle asynchronous operations in JavaScript. With promises, you can chain asynchronous operations and handle the results using `then()` and `catch()`, making the code more readable and maintainable. The same example using promises looks like this:

```javascript
asyncOperation1()
  .then(result1 => asyncOperation2(result1))
  .then(result2 => asyncOperation3(result2))
  .then(result3 => {
    // Handle the final result...
  })
  .catch(error => {
    // Handle errors...
  });
```

Using promises, each asynchronous operation is neatly separated by `.then()` without nesting callbacks. This approach is commonly referred to as "promise chaining." It significantly improves code readability and maintainability by providing a more linear flow of execution for asynchronous tasks.

Additionally, promises have error-handling capabilities with the `.catch()` method, making it easier to handle errors across the entire chain. This promotes better error handling and makes it more straightforward to debug issues in the asynchronous code.

---

### Q-6 Answer

Both `Promise.all()` and `Promise.allSettled()` are methods in JavaScript used to handle multiple promises concurrently. However, they differ in how they handle the fulfillment and rejection of the promises within the array they receive as input.

1. `Promise.all()`:
`Promise.all()` takes an iterable (usually an array) of promises as input and returns a new promise that fulfills when all the promises in the input array have fulfilled, or rejects when any one of the promises in the array rejects. The returned promise will have an array of results corresponding to the fulfillment values of the input promises, in the same order.

If any promise in the input array rejects, the entire `Promise.all()` operation fails, and the rejection reason of the first rejected promise will be propagated to the returned promise.

Example:

```javascript
const promise1 = Promise.resolve(1);
const promise2 = Promise.resolve(2);
const promise3 = Promise.reject("Error occurred!");

Promise.all([promise1, promise2, promise3])
  .then((results) => {
    console.log("All promises fulfilled:", results);
  })
  .catch((error) => {
    console.log("One of the promises rejected:", error);
  });
```

Output:
```
One of the promises rejected: Error occurred!
```

2. `Promise.allSettled()`:
`Promise.allSettled()` takes an iterable (usually an array) of promises as input and returns a new promise that fulfills with an array of objects when all the promises in the input array have either fulfilled or rejected. Each object in the resulting array will have two properties: `status` (either "fulfilled" or "rejected") and `value` (the fulfillment value or rejection reason of the corresponding promise).

This method is useful when you want to wait for all promises to settle (either fulfill or reject) without aborting the operation if any promise rejects.

Example:

```javascript
const promise1 = Promise.resolve(1);
const promise2 = Promise.resolve(2);
const promise3 = Promise.reject("Error occurred!");

Promise.allSettled([promise1, promise2, promise3])
  .then((results) => {
    console.log("All promises settled:", results);
  });
```

Output:
```
All promises settled: [
  { status: 'fulfilled', value: 1 },
  { status: 'fulfilled', value: 2 },
  { status: 'rejected', reason: 'Error occurred!' }
]
```

As you can see, `Promise.allSettled()` waits for all promises to settle and returns an array containing the status and result of each individual promise, whereas `Promise.all()` fails fast as soon as one of the promises rejects and returns the rejection reason immediately.

----

### Q-7 Answer

```javascript
function checkAge(age) {
  if (age > 80) {
    throw new SyntaxError("You are too old.");
  }
}

try {
  const age = 85;
  checkAge(age);
  console.log("You are young enough!"); 
} catch (error) {
  console.error(error.message); }
```
----

### Q-8 Answer

a. Output and Reasoning for `Promise.any()`:  

The output of this code would be `"Part 2 is resolved."`.

The `Promise.any()` method takes an iterable of promises as input and returns a single promise that resolves or rejects as soon as one of the input promises is resolved or rejects, respectively. In this code, `Promise.any()` is given an array of two promises: one that rejects after a delay of 2000 milliseconds (2 seconds) and another that resolves after a delay of 5000 milliseconds (5 seconds).

Since `Promise.any()` resolves when the first promise in the iterable resolves, it will wait for the faster promise to resolve. In this case, "Part 2 is resolved." promise is faster and will resolve after 5 seconds, while "Part 1 is rejected." would have rejected after 2 seconds. Therefore, the output will be the resolved value of the faster promise, which is `"Part 2 is resolved."`.

b. Output and Reasoning for `Promise.race()`:
The output of this code would be `"Part 1 is rejected."`.

The `Promise.race()` method takes an iterable of promises as input and returns a single promise that resolves or rejects as soon as one of the input promises resolves or rejects, respectively.

If we replace `Promise.any()` with `Promise.race()` in the given code, it will still have the same array of promises, one that rejects after 2 seconds and another that resolves after 5 seconds.

In this case, `Promise.race()` will resolve or reject based on the fastest promise, which is the promise that rejects after 2 seconds ("Part 1 is rejected."). Even though the other promise resolves with a value ("Part 2 is resolved."), it doesn't matter since `Promise.race()` only cares about the first settled promise, and rejection takes precedence over resolution.

The output for this case will be `"Part 1 is rejected."`, and it will be generated faster than in the `Promise.any()` case because `Promise.race()` resolves or rejects as soon as any of the input promises do so, and in this scenario, the rejection occurs earlier than the resolution.

---- 

### Q-9 Answer

a. The output of the above code will be:

```
Part a
```

Justification:  

In the provided code snippet, a Promise `p` is created, which takes a callback function with `resolve` and `reject` as parameters. In the callback function, there are two consecutive `resolve` calls:

```javascript
resolve("Part a");
resolve("Part b");
```

However, as mentioned earlier, only the first `resolve` call will have an effect. Once a Promise is resolved or rejected, its state becomes settled, and any subsequent calls to `resolve` or `reject` will be ignored. This means that `"Part a"` will be resolved, but `"Part b"` will not have any impact on the Promise's state.

As a result, when the `then` method is called on the Promise `p`, it will log the value resolved by the first `resolve` call, which is `"Part a"`.

b. To get both resolved results, you can use an array of promises and `Promise.all`. Here's the updated code to achieve that:

```javascript
const p1 = new Promise((resolve, reject) => {
  resolve("Part a");
});

const p2 = new Promise((resolve, reject) => {
  resolve("Part b");
});

Promise.all([p1, p2]).then((results) => {
  console.log(results[0]); // "Part a"
  console.log(results[1]); // "Part b"
});
```
---

### Q-10 Answer

To make an API request using `async/await` and `fetch()` and console the results while handling errors, you can follow this code snippet:

```javascript
async function fetchJoke() {
  try {
    const response = await fetch("https://official-joke-api.appspot.com/random_joke");
    
    if (!response.ok) {
      throw new Error("Network response was not ok.");
    }

    const data = await response.json();
    console.log("Joke:", data);
  } catch (error) {
    console.error("Error fetching joke:", error.message);
  }
}

fetchJoke();
```

Explanation:
1. We define an `async` function `fetchJoke` to encapsulate the API request.
2. Inside the function, we use the `await` keyword to make the fetch request to the API URL. The `fetch` function returns a promise that resolves with a `Response` object.
3. We check if the response status is not okay (e.g., 404 or 500 errors) using `response.ok`. If it's not okay, we throw an error using `throw new Error(...)`.
4. If the response is successful, we use `await response.json()` to extract the JSON data from the response body.
5. Finally, we log the fetched joke to the console.

Any errors that occur during the API request or JSON parsing will be caught in the `catch` block, and the corresponding error message will be logged to the console.

----
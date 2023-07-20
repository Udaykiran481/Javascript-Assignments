# Assignment-05


### Q-1  What is an IIFE (Immediately Invoked Function Expression) and why would you use it in JavaScript? Give an example of IIFE.

An IIFE, which stands for Immediately Invoked Function Expression, is a JavaScript design pattern that allows you to define and execute a function at the same time. It involves wrapping the function within parentheses and immediately invoking it by adding a pair of parentheses after it.

The primary purpose of using an IIFE is to create a new scope for the function, keeping the variables and declarations inside the function isolated from the global scope. This helps avoid naming conflicts and keeps the code modular and self-contained. It's commonly used to encapsulate code, create private variables, and avoid polluting the global namespace.


```javascript
(function() {
  // Code inside the IIFE has its own scope
  var message = "Hello, IIFE!";
  console.log(message);
})();
```

In this example, an anonymous function is wrapped within parentheses, and then immediately invoked by adding `()` after it. The function contains a variable `message` that is scoped within the function. By using an IIFE, the `message` variable is not accessible outside the function, preventing any potential conflicts with other variables in the global scope.

IIFEs are commonly used in scenarios where you need to execute code once without creating any global variables or functions. They are often used in libraries, frameworks, and modules to encapsulate code and prevent interference with other parts of the application.

----

### Q-2 What is the purpose of using the bind() method in JavaScript and how is it different from call() and apply()?

The `bind()`, `call()`, and `apply()` methods in JavaScript are all used to manipulate the context (the value of `this`) within a function. However, they differ in how they are used and their effects.

1. `bind()`: The `bind()` method creates a new function that, when called, has its `this` keyword set to a specified value. It allows you to permanently bind a function to a specific object or value. The `bind()` method returns a new function, and it does not immediately execute the function.

   Example:
   ```javascript
   const obj = {
     name: "John",
     greet: function() {
       console.log("Hello, " + this.name);
     }
   };

   const boundFunction = obj.greet.bind(obj);
   boundFunction(); // Outputs: Hello, John
   ```

2. `call()`: The `call()` method calls a function with a given `this` value and arguments provided individually (comma-separated). It immediately executes the function with the specified `this` value.

   Example:
   ```javascript
   const obj1 = {
     name: "Alice"
   };

   const obj2 = {
     name: "Bob"
   };

   function greet() {
     console.log("Hello, " + this.name);
   }

   greet.call(obj1); // Outputs: Hello, Alice
   greet.call(obj2); // Outputs: Hello, Bob
   ```

3. `apply()`: The `apply()` method is similar to `call()`, but it accepts arguments as an array instead of individual arguments. It immediately executes the function with the specified `this` value.

   Example:
   ```javascript
   const obj = {
     name: "Emily"
   };

   function greet(message) {
     console.log(message + ", " + this.name);
   }

   greet.apply(obj, ["Welcome"]); // Outputs: Welcome, Emily
   ```

---

### Q-3 What is a Higher-Order Function (HOF) in JavaScript and how is it different from regular functions? Explain with an example.

In JavaScript, a higher-order function (HOF) is a function that operates on other functions by either taking them as arguments or returning them as results. In other words, it treats functions as first-class citizens, just like any other data type.

The key distinction between higher-order functions and regular functions is that higher-order functions can manipulate and utilize functions themselves. They provide a powerful way to abstract and encapsulate common patterns of behavior, making code more concise, modular, and flexible.

Here's an example to illustrate the concept of a higher-order function in JavaScript:

```javascript
// Example 1: Higher-order function taking a function as an argument

function doOperation(operation, a, b) {
  return operation(a, b);
}

function add(x, y) {
  return x + y;
}

function subtract(x, y) {
  return x - y;
}

console.log(doOperation(add, 5, 3));      // Output: 8
console.log(doOperation(subtract, 10, 4)); // Output: 6
```

In this example, the `doOperation` function is a higher-order function that takes an operation (which is a function) as an argument, along with two operands (`a` and `b`). It then invokes the provided operation function with the given operands and returns the result.

By passing different functions (`add` and `subtract`) as arguments to `doOperation`, we can perform different operations while reusing the same higher-order function.

Another example demonstrates a higher-order function that returns a function:

```javascript
// Example 2: Higher-order function returning a function

function multiplyBy(factor) {
  return function (number) {
    return number * factor;
  };
}

const double = multiplyBy(2);
const triple = multiplyBy(3);

console.log(double(5));   // Output: 10
console.log(triple(5));   // Output: 15
```

In this example, the `multiplyBy` function is a higher-order function that takes a `factor` as an argument and returns a new function. The returned function takes a `number` as an argument and multiplies it by the `factor` provided in the outer function.

By invoking `multiplyBy` with different factors, we can create new functions (`double` and `triple`) that perform specific multiplications. These returned functions can then be called independently with their respective arguments.

In summary, higher-order functions in JavaScript enhance code flexibility and reusability by allowing functions to be treated as values. They enable powerful techniques like function composition, currying, and callbacks, which contribute to writing clean and maintainable code.

### Q-4 Write a function called multiplyBy that takes a number as input and returns a new function that multiplies any number passed into it by the original number.


```javascript
function multiplyBy(number) {
  return function(x) {
    return x * number;
  };
}
```

In this function, `multiplyBy` takes a `number` as input and returns a new function that takes another number `x` as input and returns the result of multiplying `x` by the original `number`.

You can use this function as follows:

```javascript
// Create a multiplier function for multiplying by 5
const multiplyBy5 = multiplyBy(5);

// Use the multiplier function
let result = multiplyBy5(10);
console.log(result);  // Output: 50

result = multiplyBy5(3);
console.log(result);  // Output: 15
```

In this example, we create a multiplier function `multiplyBy5` by calling `multiplyBy(5)`. We can then use `multiplyBy5` to multiply other numbers, such as `10` and `3`, which will return the respective results of `50` and `15`.

----
### Q-5 Write a function named sortArray that takes in two parameters:
1. An array of numbers
2. A boolean value ascending that indicates whether the array should be
sorted in ascending or descending order.
- The sortArray function should return the sorted array. Use an anonymous function to do the actual sorting, rather than using the built-in sort method.


```javascript
function sortArray(array, ascending) {
  const sortedArray = [];

  for (const number of array) {
    sortedArray.push(number);
  }

  for (let i = 0; i < sortedArray.length - 1; i++) {
    for (let j = i + 1; j < sortedArray.length; j++) {
      if (ascending) {
        if (sortedArray[i] > sortedArray[j]) {
          const temp = sortedArray[i];
          sortedArray[i] = sortedArray[j];
          sortedArray[j] = temp;
        }
      } else {
        if (sortedArray[i] < sortedArray[j]) {
          const temp = sortedArray[i];
          sortedArray[i] = sortedArray[j];
          sortedArray[j] = temp;
        }
      }
    }
  }

  return sortedArray;
}

const array = [1, 5, 3, 2, 4];
const ascendingArray = sortArray(array, true);
const descendingArray = sortArray(array, false);

console.log(ascendingArray);
console.log(descendingArray);
```
output:
```javascript
var numbers = [4, 2, 7, 1, 9, 5];
console.log(sortArray(numbers, true));  // Output: [1, 2, 4, 5, 7, 9]
console.log(sortArray(numbers, false)); // Output: [9, 7, 5, 4, 2, 1]
```
---


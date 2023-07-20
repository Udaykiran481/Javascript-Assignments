# Assignment-03

### Q-1 What is the difference in hoisting behaviour between a function created using functiondeclaration syntax and that created using a function expression syntax? Give an example.

**Answer**  

The main difference in hoisting behavior between a function created using function declaration syntax and a function created using function expression syntax lies in when they are accessible in the code.

Function Declaration Syntax:
When using function declaration syntax, the entire function is hoisted to the top of its scope. This means that you can call the function before its actual declaration in the code.

Example:
```javascript
hoistinFun(); // Output: "Hello!"

function hoistinFun() {
  console.log("Hello!");
}
```

In this example, even though the function call `hoistinFun` appears before the actual function declaration, it works correctly because the function declaration gets hoisted to the top of the scope.

Function Expression Syntax:
When using function expression syntax, only the variable declaration gets hoisted, not the function assignment. This means that you can access the variable before its assignment,  but you won't be able to call the function until after the assignment.

Example:
```javascript
hoistinFunExp(); // Throws an error: TypeError: hoistinFunExp is not a function

var hoistinFunExp = function() {
  console.log("Hello!");
};
```

In this example, since the function assignment `var hoistinFunExp = function() {...}` is not hoisted, when we try to call `hoistinFunExp()` before the assignment, it throws an error.

----

### Q2 Write the usage of following functions / operators and give an example.
### a. Date.now()
### b. ?? (nullish coalescing operator)
### c. ?. (optional chaining operator)

**Answer**
a. `Date.now()`: The `Date.now()` function is a built-in JavaScript method that returns the current timestamp in milliseconds. It does not require creating a new `Date` object and provides a simple way to get the current time.

Example:
```javascript
const timestamp = Date.now();
console.log(timestamp); // Outputs something like 1626534065175
```

b. `??` (nullish coalescing operator): The nullish coalescing operator `??` is a logical operator introduced in JavaScript to provide a concise way to handle nullish values (`null` or `undefined`). It returns the right-hand side operand if the left-hand side operand is `null` or `undefined`; otherwise, it returns the left-hand side operand.

Example:
```javascript
const foo = null;
const bar = foo ?? 'default value';
console.log(bar); // Outputs 'default value'

const baz = 'hello';
const qux = baz ?? 'default value';
console.log(qux); // Outputs 'hello'
```

In the first example, since `foo` is `null`, the nullish coalescing operator returns the default value `'default value'`. In the second example, `baz` is not nullish, so the value of `baz` is returned instead of the default value.

c. `?.` (optional chaining operator) in JavaScript: The optional chaining operator `?.` allows you to access properties or call methods on an object even if one of the intermediary properties is `null` or `undefined`. It short-circuits and returns `undefined` if any of the properties in the chain are not present.

Example:
```javascript
const user = {
  name: 'John',
  address: {
    city: 'New York',
    street: '123 Main St',
    zipcode: '10001'
  }
};

const cityName = user.address?.city;
console.log(cityName); // Outputs 'New York'

const phone = user.phone?.number;
console.log(phone); // Outputs undefined
```

In the first example, `user.address` exists, so `user.address?.city` returns the value `'New York'`. However, in the second example, `user.phone` is `undefined`, so `user.phone?.number` short-circuits and returns `undefined` instead of causing an error when trying to access the `number` property.

---


### Q-3 Write 2 JS statements, where:
### a. 1st one will split the words of the sentence I love going walkies into an array.
### b. 2nd one will assign the elements of the resultant array into 4 variables (in a single statement).

**Answer**

a. To split the words of the sentence "I love going walkies" into an array, you can use the `split()` method in JavaScript:

```javascript
const sentence = "I love going walkies";
const wordsArray = sentence.split(" ");
console.log(wordsArray);
```

Output:
```
["I", "love", "going", "walkies"]
```

b. To assign the elements of the resultant array into four variables in a single statement, you can use array destructuring in JavaScript:

```javascript
const [p,q,r,s] = sentence.split(" ");
console.log(p,q,r,s);
```

Output:
```
"I", "love", "going", "walkies"
```
----

### << Given object for Questions 4, 5 (and possibly 6)>>
```
const myObject = {
x1: "Samba",
x2: {
x3: {
x4: {},
x5: "Rails",
},
x6: {
x7: -1,
x8: [25, 8, 4, 10]
},
}
};

```
**Answer**
### 4-a

To perform a single line destructuring assignment to extract the value of `x3` from the given object and store it in a variable named `y`, you can use the following code:

```javascript
const { x2: { x3: y } } = myObject;
```

In this code, we are destructuring the `myObject` and accessing the nested property `x2.x3`. The value of `x2.x3` is assigned to the variable `y`.

After executing this line, you can access the value of `x3` through the `y` variable.

```javascript
console.log(y); // Output: { x4: {}, x5: "Rails" }
```

The value of `y` will be the object `{ x4: {}, x5: "Rails" }`, which represents the value of `x3` in `myObject`.

### 4-b
To perform a single line destructuring assignment to extract the 2nd element of `x8` from the given object, you can use the following code:

```javascript
const { x2: { x6: { x8: [, secondElement] } } } = myObject;
```

In this code, we are destructuring the `myObject` and accessing the nested property `x2.x6.x8`. The array `x2.x6.x8` is then destructure to obtain the 2nd element. The 2nd element is assigned to the variable `secondElement`.

After executing this line, you can access the value of the 2nd element of `x8` through the `secondElement` variable.

```javascript
console.log(secondElement); // Output: 8
```

### Q-5

**Answer**

```
const newObject = {
  ...myObject,
  x20: "Shinko",
  x21: [5, 40, 73, 19],
};

console.log(newObject);
```
output:
```
{
x1: "Samba",
x2: {
x3: {
x4: {},
x5: "Rails",
},
x6: {
x7: -1,
x8: [25, 8, 4, 10]
},
},
x20: "Shinko",
x21: [5, 40, 73, 19],
}
```
---

### Q-6

**Answer**
```
const myObject={
x1: "Samba",
x2: {
x3: {
x4: {},
x5: "Rails",
},
x6: {
x7: -1,
x8: [25, 8, 4, 10]
},
},
x20: "Shinko",
x21: [5, 40, 73, 19],
}

// Combining elements from x8 and x21 into newArray
const newArray = [...myObject.x2.x6.x8, ...myObject.x21];

console.log(newArray);

```
---
### Q-7 a

**Answer**

In the given code:

- Function f1(num) is a pure function because it takes an input (num) and returns the result of multiplying it by 3. It does not modify any external state or variables. Each time you call f1 with the same input, it will always produce the same output.

- Function f2() is an impure function because it modifies the external variable `aRandomNum` by multiplying it by 3 (`aRandomNum *= 3`). It has a side effect of changing the value of `aRandomNum` outside the function's scope. Therefore, calling f2 multiple times will produce different results.

### Q-7 b

**Answer**

Let's analyze the given JavaScript program step by step to determine the output it produces.

1. Variable Initialization:
   - `aRandomNum` is initialized with the value 37.

2. Function Definitions:
   - `f1(num)` is a function that takes a parameter `num` and logs the result of `num * 3`.
   - `f2()` is a function that multiplies the value of `aRandomNum` by 3 and logs the updated value.

3. Function Calls:
   a. `f1(aRandomNum)` is called with the value of `aRandomNum`, which is 37.
      - It will log the result of `37 * 3`, which is 111.

   b. `f2()` is called.
      - It multiplies the value of `aRandomNum` (37) by 3, resulting in `aRandomNum` being updated to 111.
      - It will log the updated value of `aRandomNum`, which is 111.

   c. `f1(aRandomNum)` is called again with the updated value of `aRandomNum`, which is 111.
      - It will log the result of `111 * 3`, which is 333.

Therefore, the output of the program will be:
```
111
111
333
```

### Q-8 In case of arrow functions, in which case the parenthesis for function parameters can be omitted? Give an example.
**Answer**  

In arrow functions, the parentheses for function parameters can be omitted when the function has exactly one parameter. This is commonly referred to as a "single parameter arrow function." 

Here's an example:

```javascript
// Arrow function with a single parameter
const square = x => x * x;

console.log(square(5)); // Output: 25
```
----

### Q-9 Can arrow functions be used as object methods? Why or why not?
**Answer**

Yes, arrow functions can be used as object methods, but there are some considerations to keep in mind when doing so.

Arrow functions have a concise syntax and lexical scoping behavior, which means they inherit the `this` value from the surrounding context where they are defined. This is different from regular functions, which have their `this` value dynamically determined at runtime based on how they are called.

When using arrow functions as object methods, the `this` value inside the arrow function will not refer to the object itself, but rather to the surrounding context where the arrow function is defined. In other words, the `this` value will not be bound to the object, which can lead to unexpected behavior.

```javascript
const obj = {
  name: 'Example Object',
  regularFunction: function() {
    console.log(this.name); // 'Example Object'
  },
  arrowFunction: () => {
    console.log(this.name); // undefined (or the value of 'name' in the outer context)
  }
};

obj.regularFunction(); // Output: 'Example Object'
obj.arrowFunction(); // Output: undefined (or the value of 'name' in the outer context)
```

In the above example, the `regularFunction` correctly accesses the `name` property of the object using `this`. However, the `arrowFunction` uses the `this` value from its surrounding context, which does not refer to the object itself. Therefore, `this.name` inside the arrow function evaluates to `undefined`.

In summary, while arrow functions can technically be used as object methods, they are not suitable when you need to access the object's properties or methods using `this`. In such cases, it is better to use regular functions to ensure the correct binding of `this` to the object.

----

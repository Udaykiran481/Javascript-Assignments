# Assignment-01 


### Q.1 Write a program that declares a variable using var, let, and const and prints the value to the console.

**Answer**
 
```
//code:

// Declaring a variable using var
var myVar = 'hello!';
console.log(myVar);

// Declaring a variable using let
let myLet = 'Hola!';
console.log(myLet);

// Declaring a variable using const
const myConst = 'Hii!';
console.log(myConst);
```

output from the console:

```
hello!
Hola!
hii!
```
---

### Q.2 Write a program that reassigns a value to a variable declared with let and prints the new value to the console.

**Answer**

```
//Code:

let myVariable = 15; // Variable declaration and initialization
console.log("Original value:", myVariable);

myVariable = 30; // Reassigning a new value
console.log("New value:", myVariable);

```
Output from the console window:

```
Original value: 15
New value: 30
```
---

### Q.3 Write a program that tries to reassign a value to a variable declared with const and prints the message to the console.

**Anwer**

```
//code:

const myVariable = 10;
myVariable = 20; // Trying to reassign a value to a const variable
console.log(myVariable);

```
In JavaScript, variables declared with the const keyword are immutable, meaning their values cannot be changed once assigned. Attempting to reassign a value to a const variable will result in an error.

console output:

```
Error: Assignment to constant variable.
```

---
### Q.4 Write a program to declare a const, let, var variable within an if statement and try to access the variable outside the if block, what is the result?

**Answer**

1. "const":  
If you declare a const variable within an if statement, it will have block scope and will not be accessible outside of the block in which it was declared.
```
if (true) {
  const x = 1;
  console.log(x);  // Output: 1
}

console.log(x);  // Throws ReferenceError: x is not defined

```

2. "let":  
Similar to const, a let variable declared within an if statement will also have block scope. However, if you try to access it outside the block, you will again receive a ReferenceError.

```
if (true) {
  let y = 3;
  console.log(y);  // Output: 3
}

console.log(y);  // Throws ReferenceError: y is not defined
```
3. "var":  
Variables declared with var have function scope or global scope, but they do not have block scope. This means that a var variable declared within an if statement will be hoisted to the nearest function scope or the global scope, making it accessible outside the if.

```
if (true) {
  var z = 6;
  console.log(z);  // Output: 6
}

console.log(z);  // Output: 6
```
---

### Q.5 Write a program that concatenates two or more strings and prints the result to the console.

**Answer**

```
//code:
string1 = "Hello, "
string2 = "world!"
string3 = " How are you?"
console.log(string1+string2+string3)

```

output from the console:

```
Hello, world! How are you?
```
----

### Q.6 Write a program that takes a string as input and prints the length of the string to the console.

**Answer**

```
//code:
function printStringLen(value) {
  console.log("Length of the string: " + value.length);
}

var input = "Hello, world!";
printStringLen(input);

```

output:
```
Length of the string: 13
```

---
### Q.7 Write a program that converts a string to uppercase and prints the result to the console.

**Answer**

```
//code:

function convertToUppercase(string) {
  var uppercaseString = string.toUpperCase();
  console.log(uppercaseString);
}

var inputString = uday;
convertToUppercase(inputString);

```
output:

```
UDAY
```

---
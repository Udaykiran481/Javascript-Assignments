# Assignment-02

### Q.1 If we execute this Javascript, what will the browser's console show?
```
code:

var text = 'outside';
function logIt(){
console.log(text);
var text = 'inside';
};
logIt();  

```
**Answer**

Executing this JavaScript code will result in the browser's console showing the output as **undefined**.

This behavior is due to variable hoisting in JavaScript. When the function logIt() is called, a local variable text is declared within the function scope using the var keyword. However, the initialization of this local variable text with the value 'inside' occurs after the console.log() statement.

Due to hoisting, the JavaScript interpreter moves the variable declaration to the top of the function scope but leaves the initialization in place. Therefore, when the console.log(text) statement is executed, the local variable text exists but has not been assigned a value yet, resulting in undefined being logged to the console.

---

### Q.2 Write a regular expression to reverse the first and last name.

**Answer**

```
//code

let name = "Uday Kiran";
let reversedName = name.replace(/^(\w+)\s+(\w+)$/, "$2 $1");
console.log(reversedName);

```

output:

```
Kiran Uday
```

- (\w+)\s+(\w+)$ is the regular expression pattern, which matches the entire name, where:  

- ^ asserts the start of the string.  
- (\w+) captures one or more word characters (letters, digits, or underscores) as the first name.
- \s+ matches one or more whitespace characters.
- (\w+) captures one or more word characters as the last name.
- $ asserts the end of the string.
- "$2 $1" is the replacement pattern, which swaps the captured first and last names. $2 refers to the second captured group (last name), and $1 refers to the first captured group (first name).

---

### Q.3 Write a Regular expression to validate email address.

**Answer**

```
//code

let email = "example@example.com";
let emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
let isValidEmail = emailRegex.test(email);
console.log(isValidEmail);

```
Output:
```
true
```

explanation:

- ^ asserts the start of the string.
- [^\s@]+ matches one or more characters that are not whitespace or '@'.
- @ matches the '@' symbol.  
- [- ^\s@]+ matches one or more characters that are not whitespace or '@'.
- \. matches the '.' symbol (it needs to be escaped with a backslash).
- [^\s@]+ matches one or more characters that are not whitespace or '@'.
- $ asserts the end of the string.
- test() method is used to test if the provided email matches the regular expression pattern. It returns true if the email is valid, and false otherwise.

---

### Q.4 Find the Output
```
var x = 100;
console.log(x);
function test(){
var x = 250;
console.log(x);
if (x > 100) {
let x = 350;
console.log(x);
}
console.log(x);
}
test();
console.log(x);
```
**Answer**

```
100
250
350
250
100

```
Explanation:

1. The variable x is declared and assigned a value of 100.
2.console.log(x) outputs the value of x, which is 100.
3.The function test() is defined.
4. Inside the test() function, a new variable x is declared and assigned a value of 250.
5. console.log(x) outputs the value of the local x, which is 250.
6. The if statement checks if the local x is greater than 100. Since it is, a new block scope is created with the let keyword.
7. Inside the block scope, another variable x is declared and assigned a value of 350.
8. console.log(x) outputs the value of the block-scoped x, which is 350.
9. After the block scope, console.log(x) outputs the value of the local x within the test() function, which is still 250.
10. Finally, console.log(x) outputs the value of the global x, which is 100

---

### Q.5 What is the difference of output between these two expressions? Give your reasons for it:
- 12 == “12”
-  12 === “12”
-  Number(12) === 12

**Answer**

- 12 == "12" is true because the == operator performs type coercion, meaning it tries to convert the operands to a common type before making the comparison.
- 12 === "12" is false because the === operator checks both the value and type, and they are not the same.
- Number(12) === 12 is true because the Number() function explicitly converts the value to a number, and the comparison between two numbers with the same value is true.

----

### Q.6 What is NaN?

**Answer**  

In JavaScript, NaN (Not a Number) is a special value that represents an invalid or unrepresentable numeric value. It is a property of the global object and is typically returned when a mathematical operation fails to produce a meaningful numeric result.  

- invalid Operations: NaN is returned when you perform arithmetic operations or calculations that involve values that cannot be represented as valid numbers.
```
var result = 0 / "abc";
console.log(result); // Output: NaN

```
Here, adding 5 to NaN yields NaN because NaN propagates through the addition operation.

- Invalid Conversions: Certain functions or operations can attempt to convert a value into a numeric representation but fail. In such cases, NaN is returned.
```
var result = parseInt("abc");
console.log(result); // Output: NaN

```
The parseInt() function attempts to parse the string "abc" into an integer, but since "abc" is not a valid numeric string, the result is NaN.

----
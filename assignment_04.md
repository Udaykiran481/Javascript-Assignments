## JS Assignment - 4 (Arrays and their built in methods)

### Q. 1 Given a string “Azad Ram Madiha Yash”. Return a string with the first letter of every word from the string. (Use built in methods).

**Answer**

```
//code:

const inputString = "Azad Ram Madiha Yash";
const words = inputString.split(" ");
const firstLetters = words.map(word => word.charAt(0));
const result = firstLetters.join("");

console.log(result); 

```
output:
```
ARMY
```
Explanation:

- The input string is stored in the inputString variable.
- We use the split() method to split the input string into an array of words based on the space character (" ").
- The map() method is used to iterate over each word in the words array and retrieve the first letter of each word using the charAt(0) method.
- The join() method is used to join the first letters into a single string, with no separator between them.
- Finally, the resulting string is stored in the result variable and printed to the console.

--- 

### Q. 2 Given an array [1, -4, 12, 0, -3, 29, -150]. Calculate the sum of all positive numbers (use built in array methods).

**Answer**

To calculate the sum of all positive numbers in the given array using built-in array methods in JavaScript, you can use the reduce() method along with an arrow function.

```
//code:

const array = [1, -4, 12, 0, -3, 29, -150];
const sumOfPositives = array.reduce((sum, num) => {
  if (num > 0) {
    return sum + num;
  }
  return sum;
}, 0);

console.log("Sum of positive numbers:", sumOfPositives);

```

output:
```
Sum of positive numbers: 42
```
---

### Q. 3 Given an array [1, 2, 3, 4, 5]. Create a new array with the square of each element(use built in array methods).

**Answer**

To create a new array with the square of each element from the given array [1, 2, 3, 4, 5], you can use the built-in map method in JavaScript. 

```
//code:
const originalArray = [1, 2, 3, 4, 5];
const squaredArray = originalArray.map((num) => num * num);
console.log(squaredArray);

```
output:
```
[1, 4, 9, 16, 25]
```
---

### Q. 4 Given an array [{ id: 2100, name: 'President Jacqueline' }, { id: 2114, name: 'Vice-president James' }, { id: 3016, name: 'House-captain Otis' }, { id: 4818, name: 'Prefect Finneas' }]. Create an array containing just the id of every individual. (write two solution one using iterator and another using built-in method).

**Answer**

Solution 1: Using an iterator (for...of loop) 

```
//code:
const data = [
  { id: 2100, name: 'President Jacqueline' },
  { id: 2114, name: 'Vice-president James' },
  { id: 3016, name: 'House-captain Otis' },
  { id: 4818, name: 'Prefect Finneas' }
];

const idArray = [];
for (const item of data) {
  idArray.push(item.id);
}

console.log(idArray);

```

output:

```
[2100, 2114, 3016, 4818]
```

Solution 2: Using the built-in map() method:

```
//code:
const data = [
  { id: 2100, name: 'President Jacqueline' },
  { id: 2114, name: 'Vice-president James' },
  { id: 3016, name: 'House-captain Otis' },
  { id: 4818, name: 'Prefect Finneas' }
];

const idArray = data.map(item => item.id);

console.log(idArray);

```
output:
```
[2100, 2114, 3016, 4818]
```
---


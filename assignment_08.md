# Assignment-08


### Q-1 Answer

```javascript
class AlertBox {
  constructor(applicationName) {
    this.applicationName = applicationName;
  }

  showAlertBox(message) {
    const formattedMessage = `${this.applicationName}: ${message}`;
    alert(formattedMessage);
  }
}

// Create a new instance of AlertBox and show a message
const appName = "NewAppilcation";
const alertBox = new AlertBox(appName);
const messageToShow = "Yayyy, Are you ready to explore!";
alertBox.showAlertBox(messageToShow);
```
---

### Q-2 Answer 

```javascript
class AlertBox {
  constructor(applicationName) {
    this.applicationName = applicationName;
  }

  showAlertBox(message) {
    const formattedMessage = `${this.applicationName}: ${message}`;
    alert(formattedMessage);
  }
}
class SuccessMessage extends AlertBox {
  showAlertBox(message) {
    const applicationName = "YourApp"; // Replace "YourApp" with the actual application name
    console.log(`${applicationName}: Success: ${message}`);
  }
}

// Create a new instance of SuccessMessage and call the showAlertBox method
const successMsg = new SuccessMessage();
successMsg.showAlertBox("Task completed successfully!");
```
---

### Q-3 Answer

Inheritance is a fundamental concept in object-oriented programming (OOP) where a class (or constructor function) can inherit properties and methods from another class. This allows the derived class to reuse the behavior of the base class, promoting code reusability and creating a hierarchical relationship between classes.

Prototypes are a mechanism that allows objects to inherit properties and methods from other objects. Each object in JavaScript has a hidden link to its prototype, which serves as a blueprint for the object. When you access a property or method on an object, JavaScript first looks for it in the object itself, and if not found, it searches for it in the prototype chain until the property or method is found or until it reaches the end of the chain (the `Object.prototype`).


```js
// Base class constructor
function Animal(name) {
  this.name = name;
}

// Base class method
Animal.prototype.sayName = function() {
  console.log(`Hi, I'm ${this.name}.`);
};

// Derived class constructor
function Dog(name, breed) {
  Animal.call(this, name); // Call the parent constructor to set the name property
  this.breed = breed;
}

// Set up inheritance: Link the Dog prototype to the Animal prototype
Dog.prototype = Object.create(Animal.prototype);

// Set the constructor property of Dog back to Dog (since it got overwritten by Object.create)
Dog.prototype.constructor = Dog;

// Add a method to the Dog prototype
Dog.prototype.bark = function() {
  console.log('Woof! Woof!');
};

// Create instances of the classes
const animal = new Animal('Generic Animal');
const dog = new Dog('Buddy', 'Golden Retriever');

// Call methods on the instances
animal.sayName(); // Output: Hi, I'm Generic Animal.
dog.sayName();    // Output: Hi, I'm Buddy.
dog.bark();       // Output: Woof! Woof.
```
---
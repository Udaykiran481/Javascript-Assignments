# Assignment-07

### Q-1 Write a JavaScript program that adds a new item to the list whenever a user inputs a text into the input field and clicks the button.

```html
<!DOCTYPE html>
<html>
<head>
<title>Add Item to List</title>
</head>
<body>
<input type="text" id="itemInput" />
<button id="addButton">Add Item</button>
<ul id="list"></ul>
<script>
const itemInput = document.getElementById("itemInput");
const addButton = document.getElementById("addButton");
const list = document.getElementById("list");

addButton.addEventListener("click", () => {
  const item = itemInput.value;
  if (item !== "") {
    const li = document.createElement("li");
    li.textContent = item;
    list.appendChild(li);
    itemInput.value = "";
  }
});
</script>
</body>
</html>
```

----

### Q-2  Write a JS function to change the font size,bg-color, and font-family for theparagraph in the HTML snippet below on clicking the button.
```
<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />
<title>JS DOM paragraph styling</title>
</head>
<body>
<p id ='text'>It is a long established fact that a reader
will be distracted by the readable content of a page when
looking at its layout. </p>
<div>
<button id="jsstyle"> Style </button>
</div>
</body>
</html>
```

To achieve the desired functionality, you can use JavaScript to add an event listener to the button. When the button is clicked, the event listener will execute a function that modifies the style properties of the paragraph element.
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>JS DOM paragraph styling</title>
</head>
<body>
  <p id="text">It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout.</p>
  <div>
    <button id="jsstyle">Style</button>
  </div>

  <script>
    document.getElementById('jsstyle').addEventListener('click', function() {
      var paragraph = document.getElementById('text');
      paragraph.style.fontSize = '24px';
      paragraph.style.backgroundColor = 'yellow';
      paragraph.style.fontFamily = 'Arial';
    });
  </script>
</body>
</html>
```
---

### Q-3 Write a JavaScript program that calculates the area of a rectangle when the user inputs the width and height into two input fields and clicks a button.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Rectangle Area Calculator</title>
    <script>
        function calculateArea() {
            // Get input values
            var width = parseFloat(document.getElementById("width").value);
            var height = parseFloat(document.getElementById("height").value);
            
            // Calculate area
            var area = width * height;
            
            // Display the result
            document.getElementById("result").textContent = "The area of the rectangle is: " + area;
        }
    </script>
</head>
<body>
    <h1>Rectangle Area Calculator</h1>
    <label for="width">Width:</label>
    <input type="number" id="width" step="any"><br><br>
    
    <label for="height">Height:</label>
    <input type="number" id="height" step="any"><br><br>
    
    <button onclick="calculateArea()">Calculate</button>
    
    <p id="result"></p>
</body>
</html>
```
---
### Q-4 Write a JavaScript program that displays an alert message to the user when they submit a form.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Form Submission Alert</title>
  <script>
    function showAlert() {
      alert("Form submitted!");
    }
  </script>
</head>
<body>
  <form onsubmit="showAlert()">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>
    <br>
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>
    <br>
    <input type="submit" value="Submit">
  </form>
</body>
</html>
```

 we define a JavaScript function called `showAlert()` that displays an alert message using the `alert()` function. The function is triggered when the form is submitted by attaching the `onsubmit` event to the `<form>` element. When the form is submitted, the `showAlert()` function is called, and the alert message "Form submitted!" will be displayed to the user.

----

### Q-5 Write a JavaScript program that displays an alert message to the user when they resize the browser window.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Resize Alert</title>
  <script>
    window.addEventListener('resize', function() {
      alert('Browser window resized!');
    });
  </script>
</head>
<body>
  <!-- Your HTML content here -->
</body>
</html>
```
In this program, we add an event listener to the `window` object for the `resize` event. Whenever the user resizes the browser window, the function provided as the second argument will be executed. Inside that function, we display an alert message using the `alert` function.

----

### Q-6 Write a JavaScript program that uses AJAX to fetch and display data from a text file when the user clicks on a button.

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8" />
<title>AJAX Text File Fetch</title>
</head>
<body>
<button id="fetch">Fetch Data</button>
<p id="data"></p>
<script>
const button = document.getElementById("fetch");
const dataParagraph = document.getElementById("data");

button.addEventListener("click", () => {
  const xhr = new XMLHttpRequest();
  xhr.open("GET", "assignment_1.md", true);
  xhr.onload = () => {
    if (xhr.status === 200) {
      dataParagraph.textContent = xhr.responseText;
    } else {
      dataParagraph.textContent = "Error fetching data";
    }
  };
  xhr.send();
});
</script>
</body>
</html>
```

### Q-7 Write a JavaScript program that uses AJAX to fetch and display an image from an API when the user clicks on a button.

```html
<!DOCTYPE html>
<html>
<head>
<title>Fetch and Display Image from API</title>
</head>
<body>
<h1>Fetch and Display Image from API</h1>
<img id="image" />
<div>
<button id="fetch-image">Fetch Image</button>
</div>
<script>
function fetchImage() {
  var xhr = new XMLHttpRequest();

  xhr.open("GET", "https://dog.ceo/api/breeds/image/random");

  xhr.responseType = "json";

  xhr.onload = function() {
    if (xhr.status === 200) {
      var data = xhr.response;
      var img = document.getElementById("image");
      img.src = data.message;
    } else {
      console.log("Error fetching image.");
    }
  };
  xhr.send();
}
var button = document.getElementById("fetch-image");
button.addEventListener("click", fetchImage);

</script>
</body>
</html>

```
----
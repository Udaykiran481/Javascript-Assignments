# Assignment-11 JQUERY

### Q-1 Answer

```html
<!DOCTYPE html>
<html>
<head>
    <title>Change Background Color</title>
    <!-- Include jQuery -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>
<body>
    <button id="clickMe">Click Me!</button>

    <script>
        $(document).ready(function() {
            // Attach a click event handler to the button with ID "clickMe"
            $("#clickMe").on("click", function() {
                // Change the background color of the body element to red
                $("body").css("background-color", "red");
            });
        });
    </script>
</body>
</html>
```

In this code, we include the jQuery library using a script tag. Then, we use the `$(document).ready()` function to ensure that the JavaScript code inside it runs only after the document (HTML) is fully loaded. Inside the `ready` function, we use the `$("#clickMe")` selector to target the button with the ID "clickMe" and attach a click event handler to it using the `.on()` method. When the button is clicked, the `function()` is executed, and we use `$("body").css("background-color", "red");` to change the background color of the body element to red.

### Q-2 Answer

To achieve this using jQuery, you can use the `text()` and `append()` methods. The `text()` method is used to get the text content of an element, and the `append()` method is used to insert content at the end of the selected element. Here's the jQuery function:

```html
<!DOCTYPE html>
<html>
<head>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>
<body>
  <p id="myPara">This is the original paragraph.</p>
  
  <script>
    $(document).ready(function() {
      var originalText = $("#myPara").text();
      var newParagraph = $("<p>").attr("id", "newPara");
      newParagraph.text(originalText);
      $("#myPara").after(newParagraph);
    });
  </script>
</body>
</html>
```

output:


```
This is the original paragraph.
This is the original paragraph.
```
---

### Q-3 Answer


```html
<!DOCTYPE html>
<html>
<head>
  <title>Text Input Form</title>
</head>
<body>
  <form id="myForm">
    <label for="myInput">Enter your text:</label>
    <input type="text" id="myInput" name="userText">
    <input type="submit" value="Submit">
  </form>

  <!-- Include jQuery -->
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

  <!-- jQuery function to handle form submission -->
  <script>
    $(document).ready(function() {
      $("#myForm").submit(function(event) {
        event.preventDefault();
        var userText = $("#myInput").val();
        alert("You entered: " + userText);
      });
    });
  </script>
</body>
</html>
```
---

### Q-4 Answer

HTML:
```html
<!DOCTYPE html>
<html>
<head>
  <title>Highlight First and Last List Items</title>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>
<body>
  <ul id="myList">
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
    <li>Item 5</li>
  </ul>

  <script src="script.js"></script>
</body>
</html>
```

JavaScript (script.js):
```js
$(document).ready(function() {
  // Function to highlight the first and last list items with red color
  function highlightFirstAndLast() {
    var listItems = $("#myList li");

    // Remove any existing highlight
    listItems.removeClass("highlight");

    // Highlight the first and last list items
    listItems.first().addClass("highlight");
    listItems.last().addClass("highlight");
  }

  // Call the function when the document is ready
  highlightFirstAndLast();
});
```

CSS (style.css):
```css
/* Define the CSS class to apply the red color */
.highlight {
  color: red;
}
```
----

### Q-5 Answer 

HTML:
```html
<!DOCTYPE html>
<html>
<head>
  <title>Adding Rows to Table</title>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>
<body>
  <table id="myTable">
    <thead>
      <tr>
        <th>Name</th>
        <th>Age</th>
        <th>Occupation</th>
      </tr>
    </thead>
    <tbody>
      <!-- Existing rows will be added here -->
    </tbody>
  </table>

  <button id="addRowBtn">Add Row</button>

  <script src="script.js"></script>
</body>
</html>
```

JavaScript (script.js):
```js
$(document).ready(function() {
  function addRowToTable(name, age, occupation) {
    var newRow = '<tr>' +
                  '<td>' + name + '</td>' +
                  '<td>' + age + '</td>' +
                  '<td>' + occupation + '</td>' +
                 '</tr>';
    $('#myTable tbody').append(newRow);
  }
  $('#addRowBtn').on('click', function() {
    addRowToTable('John', '30', 'Developer');
  });
});
```
----
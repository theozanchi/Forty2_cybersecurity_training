# Fixing this XSS vulnerability

To fix this vulnerability, the lines that append user input to the script have to be deleted (commented here) below.

The user input also need to be sanitized to prevent a user from injecting scripts by using the following syntax: 
```js
<script>...</script>
```

Here is the corrected HTML file:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Vulnerable XSS Example</title>
</head>
<body>
    <h1>XSS Vulnerability Example</h1>
    <p>This is a vulnerable page with an XSS vulnerability.</p>
    <form>
        <label for="inputText">Enter some text:</label>
        <input type="text" id="inputText">
        <button type="button" onclick="displayText()">Submit</button>
    </form>
    <div id="output"></div>
    <script>
        document.cookie = "ftCookies=If_You_See_Me_Its_Win";
        function displayText() {
            var userInput = document.getElementById("inputText").value;
            var sanitizedInput = sanitizeInput(userInput);
            document.getElementById("output").innerHTML = "<b>" + sanitizedInput + "</b>";

            //var script = document.createElement("script");
            //script.textContent = userInput;
            //document.body.appendChild(script);

            function sanitizeInput(input) {
            // Replace < and > with HTML entities to prevent XSS
            return input.replace(/</g, "&lt;").replace(/>/g, "&gt;");
            }
        }
    </script>

    <div id="cookieOutput"></div>
</body>
</html>
```
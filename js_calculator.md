Creating a simple web calculator that allows users to perform basic arithmetic operations (addition, subtraction, multiplication, and division) is a fun and educational project. Below is a complete example of a web calculator implemented using HTML, CSS, and JavaScript.

### Step-by-Step Guide

### 1. Set Up the Project

Create a new HTML file named `calculator.html` and open it in your favorite code editor.

### 2. Basic HTML Structure

Add the following HTML structure for the calculator.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Web Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4; /* Light background */
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0; /* Remove default margin */
        }

        .calculator {
            background: #fff; /* White background */
            padding: 20px; /* Padding around the calculator */
            border-radius: 10px; /* Rounded corners */
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); /* Shadow effect */
            width: 300px; /* Fixed width for the calculator */
            text-align: center; /* Center align text */
        }

        input[type="number"] {
            width: 100%; /* Full width */
            padding: 10px; /* Inner padding */
            margin: 10px 0; /* Space between inputs */
            border: 1px solid #ccc; /* Light border */
            border-radius: 5px; /* Rounded corners */
            font-size: 16px; /* Increase font size */
        }

        button {
            width: 48%; /* Button width */
            padding: 10px; /* Inner padding */
            margin: 5px; /* Space between buttons */
            border: none; /* Remove border */
            border-radius: 5px; /* Rounded corners */
            background-color: #007bff; /* Blue background */
            color: white; /* White text */
            cursor: pointer; /* Pointer on hover */
            font-size: 16px; /* Increase font size */
        }

        button:hover {
            background-color: #0056b3; /* Darker blue on hover */
        }

        .result {
            margin-top: 20px; /* Space above result */
            font-size: 1.5em; /* Larger font for result */
        }
    </style>
</head>
<body>

    <div class="calculator">
        <h2>Simple Calculator</h2>
        <input type="number" id="num1" placeholder="Enter first number" required>
        <input type="number" id="num2" placeholder="Enter second number" required>
        
        <button onclick="calculate('add')">+</button>
        <button onclick="calculate('subtract')">-</button>
        <button onclick="calculate('multiply')">*</button>
        <button onclick="calculate('divide')">/</button>
        
        <div class="result" id="result"></div>
    </div>

    <script>
        function calculate(operation) {
            const num1 = parseFloat(document.getElementById("num1").value);
            const num2 = parseFloat(document.getElementById("num2").value);
            let result;

            if (isNaN(num1) || isNaN(num2)) {
                document.getElementById("result").textContent = "Please enter valid numbers.";
                return;
            }

            switch (operation) {
                case 'add':
                    result = num1 + num2;
                    break;
                case 'subtract':
                    result = num1 - num2;
                    break;
                case 'multiply':
                    result = num1 * num2;
                    break;
                case 'divide':
                    if (num2 === 0) {
                        document.getElementById("result").textContent = "Cannot divide by zero!";
                        return;
                    }
                    result = num1 / num2;
                    break;
                default:
                    result = "Invalid operation.";
            }

            document.getElementById("result").textContent = `Result: ${result}`;
        }
    </script>
</body>
</html>
```

### Explanation of the Code:

1. **HTML Structure**:
   - The calculator consists of two input fields for numbers and buttons for each arithmetic operation. The result will be displayed in a dedicated `<div>`.

2. **CSS Styles**:
   - Basic styles create a clean and centered layout for the calculator. Buttons change color on hover for better user interaction, and the result text is styled for prominence.

3. **JavaScript Functionality**:
   - **`calculate(operation)`**: This function is called when any of the operation buttons are clicked. It retrieves the values from the input fields, parses them as floats, and checks if they are valid numbers.
   - Depending on the operation selected, the appropriate arithmetic calculation is performed. If division is chosen and the second number is zero, an error message is displayed.
   - Finally, the result is displayed in the result `<div>`.

### 3. Open Your Calculator in a Browser

To see your calculator in action, open the `calculator.html` file in a web browser. You should be able to:
- Enter two numbers.
- Click the buttons for addition, subtraction, multiplication, or division to see the result displayed.

### Conclusion

You’ve successfully created a simple web calculator that performs basic arithmetic operations. This project can be further enhanced by adding features such as keyboard input support, a clear button to reset the calculator, or even more advanced mathematical functions. Enjoy building and enhancing your calculator!

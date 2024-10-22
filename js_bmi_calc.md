Creating a web application for BMI (Body Mass Index) calculation using JavaScript is a great way to practice your skills in HTML, CSS, and JavaScript. Below is a complete example of a simple BMI calculator that allows users to input their height and weight, then calculates and displays their BMI.

### Step-by-Step Guide

### 1. Set Up the Project

Create a new HTML file named `bmi-calculator.html` and open it in your favorite code editor.

### 2. Basic HTML Structure

Add the following HTML structure for the BMI calculator.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMI Calculator</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4; /* Light background */
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .container {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            max-width: 400px; /* Set max width */
            text-align: center; /* Center align text */
        }

        input[type="number"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        button {
            padding: 10px 15px;
            background-color: #007bff; /* Blue */
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        button:hover {
            background-color: #0056b3; /* Darker blue */
        }

        .result {
            margin-top: 20px;
            font-size: 1.5em; /* Increase font size */
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>BMI Calculator</h2>
        <input type="number" id="weight" placeholder="Weight (kg)" required>
        <input type="number" id="height" placeholder="Height (m)" required>
        <button onclick="calculateBMI()">Calculate BMI</button>
        <div class="result" id="result"></div>
    </div>

    <script>
        function calculateBMI() {
            const weight = parseFloat(document.getElementById("weight").value);
            const height = parseFloat(document.getElementById("height").value);

            if (isNaN(weight) || isNaN(height) || height <= 0) {
                alert("Please enter valid weight and height.");
                return;
            }

            const bmi = (weight / (height * height)).toFixed(2); // Calculate BMI and round to 2 decimal places

            let resultText;
            if (bmi < 18.5) {
                resultText = `Your BMI is ${bmi}. You are underweight.`;
            } else if (bmi < 24.9) {
                resultText = `Your BMI is ${bmi}. You have a normal weight.`;
            } else if (bmi < 29.9) {
                resultText = `Your BMI is ${bmi}. You are overweight.`;
            } else {
                resultText = `Your BMI is ${bmi}. You are obese.`;
            }

            document.getElementById("result").textContent = resultText; // Display the result
        }
    </script>
</body>
</html>
```

### Explanation of the Code:

1. **HTML Structure**:
   - The application contains input fields for the user to enter their weight and height, a button to calculate the BMI, and a div to display the result.

2. **CSS Styles**:
   - Basic styles create a clean and user-friendly layout for the BMI calculator. The layout is centered on the page, and the button changes color on hover for better interaction.

3. **JavaScript Functionality**:
   - **`calculateBMI()`**: This function retrieves the weight and height values from the input fields. It checks if the inputs are valid (not NaN and height > 0). If valid, it calculates the BMI using the formula \( \text{BMI} = \frac{\text{weight}}{\text{height}^2} \) and rounds it to two decimal places.
   - The function then generates a result text based on the calculated BMI value, categorizing it into underweight, normal weight, overweight, or obese.
   - Finally, it updates the content of the result div with the calculated BMI and the corresponding category.

### 4. Open Your BMI Calculator in a Browser

To see your BMI calculator in action, open the `bmi-calculator.html` file in a web browser. You should be able to:
- Enter your weight and height.
- Click "Calculate BMI" to see your BMI and the corresponding category displayed.

### Conclusion

You've successfully created a BMI calculator using JavaScript! This simple application can be expanded with features like storing past calculations, adding more user inputs (like age and activity level), or styling it further with CSS frameworks like Bootstrap. Enjoy building and improving your BMI calculator!

Adding a “Sign Up” button to an event registration page that changes color and size on hover is a great way to enhance user interaction. Below is an example of how to implement this using HTML and CSS.

### Step-by-Step Guide

### 1. Set Up the Project

Create a new HTML file named `event-registration.html` and open it in your favorite code editor.

### 2. Basic HTML Structure

Add the following HTML structure for the event registration page with a "Sign Up" button.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Registration</title>
    <style>
        body {
            font-family: Arial, sans-serif; /* Set font for the page */
            background-color: #f0f8ff; /* Light background color */
            color: #333; /* Default text color */
            margin: 0; /* Remove default margin */
            padding: 20px; /* Padding around the content */
            text-align: center; /* Center align text */
        }

        h1 {
            font-size: 2.5em; /* Heading size */
            margin-bottom: 20px; /* Space below heading */
        }

        p {
            font-size: 1.2em; /* Paragraph size */
            margin-bottom: 30px; /* Space below paragraph */
        }

        .signup-button {
            background-color: #28a745; /* Initial button color (green) */
            color: white; /* Button text color */
            padding: 15px 30px; /* Padding for button */
            font-size: 1.2em; /* Button text size */
            border: none; /* Remove border */
            border-radius: 5px; /* Rounded corners */
            cursor: pointer; /* Pointer on hover */
            transition: background-color 0.3s, transform 0.3s; /* Smooth transition for background and size */
        }

        .signup-button:hover {
            background-color: #218838; /* Darker green on hover */
            transform: scale(1.1); /* Slightly increase button size */
        }
    </style>
</head>
<body>

    <h1>Event Registration</h1>
    <p>Join us for an exciting event! Fill out the form below to secure your spot.</p>
    <button class="signup-button">Sign Up</button>

</body>
</html>
```

### Explanation of the Code:

1. **HTML Structure**:
   - The page includes a heading, a description, and a button with the text "Sign Up".

2. **CSS Styles**:
   - **Body Styles**: Sets a light background color and centers the text.
   - **Heading and Paragraph**: Styles the heading and paragraph for visibility and spacing.
   - **Button Styles**: 
     - The button starts with a green background and transitions to a darker green when hovered.
     - The `transform: scale(1.1);` increases the button size by 10% when hovered over, giving a nice visual feedback effect.
     - The `transition` property is used to create a smooth animation effect when changing colors and sizes.

### 3. Open Your Event Registration Page in a Browser

To see your event registration page with the "Sign Up" button in action, open the `event-registration.html` file in a web browser. When you hover over the button, it should change color and size as specified.

### Conclusion

You’ve successfully created an event registration page with a dynamic "Sign Up" button. You can further enhance this page by adding a registration form, additional styling, or JavaScript for form handling. Enjoy building your event registration page!

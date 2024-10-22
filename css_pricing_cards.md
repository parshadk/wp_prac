Creating a subscription plan comparison for a SaaS product is an excellent way to showcase the features of different plans clearly and attractively. Below, I provide a complete example using HTML and CSS to display a comparison of Basic, Pro, and Enterprise plans with distinct colors and layouts.

### Step-by-Step Guide

### 1. Set Up the Project

Create a new HTML file named `subscription-plans.html` and open it in your favorite code editor.

### 2. Basic HTML Structure

Add the following HTML structure for the subscription plan comparison.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Subscription Plan Comparison</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4; /* Light background */
            margin: 0; /* Remove default margin */
            padding: 20px; /* Padding around the content */
        }

        .plans-container {
            display: flex; /* Use flexbox for layout */
            justify-content: center; /* Center the plans */
            gap: 20px; /* Space between plans */
            max-width: 1200px; /* Max width for the container */
            margin: auto; /* Center the container */
        }

        .plan {
            background: white; /* White background for plans */
            border-radius: 10px; /* Rounded corners */
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); /* Shadow effect */
            padding: 20px; /* Inner padding */
            text-align: center; /* Center align text */
            flex: 1; /* Allow plans to grow */
            min-width: 250px; /* Minimum width for responsive design */
        }

        .plan h2 {
            margin: 0 0 10px; /* Space below the heading */
        }

        .basic {
            border: 2px solid #007bff; /* Blue border for Basic */
        }

        .pro {
            border: 2px solid #28a745; /* Green border for Pro */
        }

        .enterprise {
            border: 2px solid #dc3545; /* Red border for Enterprise */
        }

        .features {
            list-style-type: none; /* Remove bullet points */
            padding: 0; /* Remove default padding */
            margin: 20px 0; /* Space around features list */
        }

        .features li {
            padding: 10px; /* Padding for each feature */
            border-bottom: 1px solid #ddd; /* Bottom border for separation */
        }

        .features li:last-child {
            border-bottom: none; /* Remove bottom border from last item */
        }

        .button {
            display: inline-block; /* Center the button */
            background-color: #007bff; /* Button background */
            color: white; /* Button text color */
            padding: 10px 20px; /* Button padding */
            text-decoration: none; /* Remove underline */
            border-radius: 5px; /* Rounded corners for button */
            margin-top: 10px; /* Space above button */
        }

        .button:hover {
            background-color: #0056b3; /* Darker blue on hover */
        }
    </style>
</head>
<body>

    <h1 style="text-align: center;">Subscription Plans Comparison</h1>
    <div class="plans-container">
        <div class="plan basic">
            <h2>Basic Plan</h2>
            <p>$10/month</p>
            <ul class="features">
                <li>Feature 1: Basic Support</li>
                <li>Feature 2: 5 GB Storage</li>
                <li>Feature 3: 1 User</li>
                <li>Feature 4: Access to Basic Features</li>
            </ul>
            <a href="#" class="button">Choose Basic</a>
        </div>

        <div class="plan pro">
            <h2>Pro Plan</h2>
            <p>$25/month</p>
            <ul class="features">
                <li>Feature 1: Priority Support</li>
                <li>Feature 2: 50 GB Storage</li>
                <li>Feature 3: Up to 5 Users</li>
                <li>Feature 4: Access to All Basic Features</li>
                <li>Feature 5: Access to Pro Features</li>
            </ul>
            <a href="#" class="button">Choose Pro</a>
        </div>

        <div class="plan enterprise">
            <h2>Enterprise Plan</h2>
            <p>$50/month</p>
            <ul class="features">
                <li>Feature 1: 24/7 Support</li>
                <li>Feature 2: Unlimited Storage</li>
                <li>Feature 3: Unlimited Users</li>
                <li>Feature 4: Access to All Features</li>
                <li>Feature 5: Custom Solutions</li>
            </ul>
            <a href="#" class="button">Choose Enterprise</a>
        </div>
    </div>

</body>
</html>
```

### Explanation of the Code:

1. **HTML Structure**:
   - The comparison is organized into three main sections, each representing a subscription plan (Basic, Pro, and Enterprise). Each plan is wrapped in a `<div>` with the class `plan`, and features are listed using an unordered list (`<ul>`).

2. **CSS Styles**:
   - The styles create a responsive layout using Flexbox, allowing the plans to align nicely side by side.
   - Each plan has a distinct border color to differentiate them visually.
   - The button style enhances the call-to-action, making it clear and appealing.

3. **Responsive Design**:
   - The `flex: 1` property allows each plan to grow and occupy equal space in the container, while `min-width` ensures the plans do not get too narrow on smaller screens.

### 3. Open Your Subscription Plans in a Browser

To see your subscription plan comparison in action, open the `subscription-plans.html` file in a web browser. You should see a visually appealing layout with clear distinctions between the Basic, Pro, and Enterprise plans, each highlighting its features.

### Conclusion

You’ve successfully created a subscription plan comparison for a SaaS product, showcasing different pricing tiers and their features in a visually distinct layout. You can further enhance this project by adding additional features such as tooltips for each feature, user testimonials, or animations for the buttons. Enjoy building and improving your subscription plan comparison!

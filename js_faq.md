Creating a dynamic FAQ section where clicking on each question reveals the answer and hovering over the question highlights it is a great way to improve user interaction on your website. Below is a complete example that demonstrates how to implement this functionality using HTML, CSS, and JavaScript.

### Step-by-Step Guide

### 1. Set Up the Project

Create a new HTML file named `faq.html` and open it in your favorite code editor.

### 2. Basic HTML Structure

Add the following HTML structure for the FAQ section.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dynamic FAQ Section</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4; /* Light background */
            margin: 0;
            padding: 20px; /* Padding around the content */
        }

        .faq-container {
            max-width: 600px; /* Set maximum width */
            margin: auto; /* Center the container */
            background: #fff; /* White background */
            border-radius: 8px; /* Rounded corners */
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); /* Shadow effect */
            padding: 20px; /* Inner padding */
        }

        .faq-question {
            cursor: pointer; /* Change cursor to pointer */
            padding: 10px; /* Padding around questions */
            border: 1px solid #ccc; /* Light border */
            margin-bottom: 10px; /* Space between questions */
            border-radius: 5px; /* Rounded corners */
            transition: background-color 0.3s; /* Smooth transition */
        }

        .faq-answer {
            display: none; /* Hide answers initially */
            padding: 10px; /* Padding around answers */
            border-left: 3px solid #007bff; /* Left border for answers */
            background-color: #f9f9f9; /* Light background for answers */
        }

        .faq-question:hover {
            background-color: #e0f7fa; /* Highlight on hover */
        }

        .active {
            background-color: #b2ebf2; /* Highlight for active question */
        }
    </style>
</head>
<body>

    <div class="faq-container">
        <h2>Frequently Asked Questions</h2>

        <div class="faq-question" onclick="toggleAnswer(this)">
            What is your return policy?
        </div>
        <div class="faq-answer">
            We accept returns within 30 days of purchase. Items must be unused and in their original packaging.
        </div>

        <div class="faq-question" onclick="toggleAnswer(this)">
            How long does shipping take?
        </div>
        <div class="faq-answer">
            Shipping typically takes 5-7 business days, depending on your location and the shipping method chosen.
        </div>

        <div class="faq-question" onclick="toggleAnswer(this)">
            Do you ship internationally?
        </div>
        <div class="faq-answer">
            Yes, we ship to several countries. Please check our shipping policy for more details.
        </div>

        <div class="faq-question" onclick="toggleAnswer(this)">
            How can I contact customer support?
        </div>
        <div class="faq-answer">
            You can reach our customer support team via the contact form on our website or by emailing support@example.com.
        </div>
    </div>

    <script>
        function toggleAnswer(questionElement) {
            // Toggle the corresponding answer visibility
            const answerElement = questionElement.nextElementSibling;
            answerElement.style.display = answerElement.style.display === "block" ? "none" : "block";

            // Highlight the active question
            const allQuestions = document.querySelectorAll('.faq-question');
            allQuestions.forEach(q => {
                if (q !== questionElement) {
                    q.classList.remove('active'); // Remove highlight from others
                }
            });
            questionElement.classList.toggle('active'); // Toggle highlight for the clicked question
        }
    </script>
</body>
</html>
```

### Explanation of the Code:

1. **HTML Structure**:
   - The FAQ section consists of a container with several questions and corresponding answers. Each question is wrapped in a `<div>` with the class `faq-question`, and each answer is in a `<div>` with the class `faq-answer`.

2. **CSS Styles**:
   - The styles create a clean layout for the FAQ section, including hover effects and transitions. Questions change background color on hover, and active questions get a distinct highlight.

3. **JavaScript Functionality**:
   - **`toggleAnswer(questionElement)`**: This function is triggered when a question is clicked. It toggles the visibility of the corresponding answer by changing its `display` property. If the answer is currently displayed (`block`), it hides it by setting it to `none`, and vice versa.
   - It also highlights the active question by adding or removing the `active` class based on whether it’s clicked or not. All other questions have the active class removed, ensuring only the clicked question is highlighted.

### 3. Open Your FAQ Section in a Browser

To see your dynamic FAQ section in action, open the `faq.html` file in a web browser. You should be able to:
- Click on each question to reveal or hide the corresponding answer.
- Hover over questions to see the highlight effect.

### Conclusion

You’ve successfully implemented a dynamic FAQ section with click-to-reveal answers and hover highlights. This feature can significantly enhance user experience by providing quick access to information. You can further improve this project by adding animations, expanding the number of FAQs, or fetching data from an external source. Enjoy building and enhancing your FAQ section!

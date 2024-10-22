Creating a personal portfolio that showcases your work with a grid layout is a great way to display your projects dynamically. Below, I’ll guide you through designing a responsive personal portfolio using HTML and CSS.

### Step-by-Step Guide

### 1. Set Up the Project

Create a new HTML file named `portfolio.html` and open it in your favorite code editor.

### 2. Basic HTML Structure

Add the following HTML structure for your portfolio page.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif; /* Set font */
            margin: 0; /* Remove default margin */
            padding: 20px; /* Padding around the content */
            background-color: #f0f0f0; /* Light background color */
            color: #333; /* Text color */
        }

        h1 {
            text-align: center; /* Center align the heading */
            font-size: 2.5em; /* Heading size */
            margin-bottom: 30px; /* Space below heading */
            color: #2c3e50; /* Dark blue color for heading */
        }

        .portfolio-grid {
            display: grid; /* Use grid layout */
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); /* Responsive grid */
            gap: 20px; /* Space between grid items */
        }

        .portfolio-item {
            background-color: white; /* White background for items */
            border-radius: 8px; /* Rounded corners */
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* Subtle shadow */
            overflow: hidden; /* Clip overflowing content */
            transition: transform 0.2s; /* Smooth transform */
        }

        .portfolio-item:hover {
            transform: scale(1.05); /* Scale up on hover */
        }

        .portfolio-image {
            width: 100%; /* Full width image */
            height: 200px; /* Fixed height for images */
            object-fit: cover; /* Cover the area */
        }

        .portfolio-description {
            padding: 15px; /* Padding inside items */
            text-align: center; /* Center text */
        }

        .portfolio-description h2 {
            font-size: 1.5em; /* Subheading size */
            margin: 10px 0; /* Margin above and below */
            color: #34495e; /* Slightly lighter blue */
        }

        .portfolio-description p {
            font-size: 1em; /* Paragraph size */
            margin: 0; /* Remove margin */
        }

        /* Responsive Design */
        @media (max-width: 600px) {
            h1 {
                font-size: 2em; /* Smaller heading size */
            }
        }
    </style>
</head>
<body>

    <h1>My Portfolio</h1>
    <div class="portfolio-grid">
        <div class="portfolio-item">
            <img src="https://via.placeholder.com/300" alt="Project 1" class="portfolio-image"> <!-- Replace with actual project image -->
            <div class="portfolio-description">
                <h2>Project Title 1</h2>
                <p>A brief description of the project, its features, and technologies used.</p>
            </div>
        </div>

        <div class="portfolio-item">
            <img src="https://via.placeholder.com/300" alt="Project 2" class="portfolio-image"> <!-- Replace with actual project image -->
            <div class="portfolio-description">
                <h2>Project Title 2</h2>
                <p>A brief description of the project, its features, and technologies used.</p>
            </div>
        </div>

        <div class="portfolio-item">
            <img src="https://via.placeholder.com/300" alt="Project 3" class="portfolio-image"> <!-- Replace with actual project image -->
            <div class="portfolio-description">
                <h2>Project Title 3</h2>
                <p>A brief description of the project, its features, and technologies used.</p>
            </div>
        </div>

        <div class="portfolio-item">
            <img src="https://via.placeholder.com/300" alt="Project 4" class="portfolio-image"> <!-- Replace with actual project image -->
            <div class="portfolio-description">
                <h2>Project Title 4</h2>
                <p>A brief description of the project, its features, and technologies used.</p>
            </div>
        </div>

        <!-- Add more portfolio items as needed -->
    </div>

</body>
</html>
```

### Explanation of the Code:

1. **HTML Structure**:
   - The page includes a heading and a grid of portfolio items. Each item contains an image and a description.

2. **CSS Styles**:
   - **Body Styles**: Sets a light background color, font, and margin.
   - **Grid Layout**: The `.portfolio-grid` class uses CSS Grid to create a responsive layout. The grid will automatically fill the available space with a minimum width of 300px for each item.
   - **Portfolio Items**: Each item has a white background, rounded corners, and a subtle shadow. When hovered, it scales up slightly for a dynamic effect.
   - **Image Styles**: The images are set to cover their containers while maintaining aspect ratio.
   - **Description Styles**: Centered text with appropriate margins and sizes for headings and paragraphs.
   - **Responsive Design**: Media queries adjust the heading size for smaller screens.

### 3. Open Your Portfolio Page in a Browser

To see your portfolio in action, open the `portfolio.html` file in a web browser. You should see a well-structured and styled portfolio that adjusts to different screen sizes.

### Conclusion

You’ve successfully created a personal portfolio showcasing your work in a responsive grid layout. You can enhance this project by adding more projects, links to live demos or GitHub repositories, and additional styling for a more personalized look. Enjoy building and customizing your portfolio!

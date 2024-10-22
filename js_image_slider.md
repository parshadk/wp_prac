Creating a simple image slideshow for a real estate website is a great way to showcase different property images. Below is a complete example that demonstrates how to implement a rotating image banner using HTML, CSS, and JavaScript.

### Step-by-Step Guide

### 1. Set Up the Project

Create a new HTML file named `index.html` and open it in your favorite code editor.

### 2. Basic HTML Structure

Add the following HTML structure for the image slideshow. This includes a container for the slideshow and buttons for navigation.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Real Estate Image Slideshow</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4; /* Light background */
            margin: 0;
            padding: 0;
        }

        .slideshow-container {
            position: relative;
            max-width: 1000px;
            margin: auto;
            overflow: hidden;
            border-radius: 10px; /* Rounded corners */
        }

        .slides {
            display: none;
            width: 100%;
        }

        .active {
            display: block; /* Show active slide */
        }

        .prev, .next {
            cursor: pointer;
            position: absolute;
            top: 50%;
            width: auto;
            padding: 16px;
            color: white;
            font-weight: bold;
            font-size: 18px;
            transition: 0.6s ease;
            border-radius: 0 3px 3px 0;
            user-select: none; /* Prevent text selection */
        }

        .next {
            right: 0;
            border-radius: 3px 0 0 3px;
        }

        .prev:hover, .next:hover {
            background-color: rgba(0, 0, 0, 0.8); /* Dark background on hover */
        }

        .caption {
            color: #fff;
            font-size: 20px;
            text-align: center;
            background-color: rgba(0, 0, 0, 0.5); /* Semi-transparent background */
            padding: 10px;
            position: absolute;
            bottom: 0;
            width: 100%;
        }

        /* Optional: Style for the images */
        img {
            width: 100%;
            height: auto;
        }
    </style>
</head>
<body>

    <div class="slideshow-container">
        <div class="slides active">
            <img src="https://via.placeholder.com/1000x500?text=Property+1" alt="Property 1">
            <div class="caption">Beautiful Family Home</div>
        </div>

        <div class="slides">
            <img src="https://via.placeholder.com/1000x500?text=Property+2" alt="Property 2">
            <div class="caption">Luxury Apartment</div>
        </div>

        <div class="slides">
            <img src="https://via.placeholder.com/1000x500?text=Property+3" alt="Property 3">
            <div class="caption">Modern Villa</div>
        </div>

        <a class="prev" onclick="changeSlide(-1)">&#10094;</a>
        <a class="next" onclick="changeSlide(1)">&#10095;</a>
    </div>

    <script src="script.js"></script>
    <script>
        let slideIndex = 0;
        showSlides();

        function showSlides() {
            const slides = document.getElementsByClassName("slides");
            for (let i = 0; i < slides.length; i++) {
                slides[i].style.display = "none";  // Hide all slides
            }
            slideIndex++;
            if (slideIndex >= slides.length) {slideIndex = 0;}  // Reset to first slide
            slides[slideIndex].style.display = "block";  // Show current slide
            setTimeout(showSlides, 3000);  // Change slide every 3 seconds
        }

        function changeSlide(n) {
            slideIndex += n;  // Adjust index based on button click
            if (slideIndex < 0) { slideIndex = slides.length - 1; }  // Loop back to last slide
            if (slideIndex >= slides.length) { slideIndex = 0; }  // Loop back to first slide
            showSlides();  // Show updated slide
        }
    </script>
</body>
</html>
```

### Explanation of the Code:

1. **HTML Structure**:
   - The slideshow is contained within a `<div class="slideshow-container">`.
   - Each slide is represented by a `<div class="slides">`, which includes an image and a caption.
   - Navigation arrows are implemented as `<a>` elements with the `prev` and `next` classes.

2. **CSS Styles**:
   - The slideshow container has a relative position, while each slide is set to `display: none` to hide them initially.
   - The `.active` class is used to display the currently active slide.
   - Navigation arrows are styled to be positioned on the left and right sides of the slideshow.

3. **JavaScript Functionality**:
   - The `showSlides` function controls the automatic transition between slides, setting the current slide to display and hiding the others.
   - The `changeSlide` function adjusts the `slideIndex` based on which arrow is clicked and shows the appropriate slide.
   - The slideshow automatically changes slides every 3 seconds using `setTimeout`.

### 3. Open Your Real Estate Slideshow in a Browser

To see your image slideshow in action, open the `index.html` file in a web browser. You should see a rotating image banner showcasing different property images with navigation arrows to manually change the slides.

### Conclusion

You’ve successfully created a simple image slideshow for a real estate website using JavaScript and CSS. This slideshow can be customized further by adding more images, styles, or additional features like dots for navigation. Enjoy showcasing your properties!

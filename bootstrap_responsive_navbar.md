Creating a responsive navigation bar using Bootstrap is straightforward and helps ensure your cafe website is user-friendly on all devices. Below is a step-by-step guide to designing a website for a cafe with a collapsible navigation bar that adapts to smaller screens using Bootstrap's navbar component.

### Step-by-Step Guide

### 1. Set Up the Project

Create a new HTML file, for example, `index.html`, and open it in your favorite code editor.

### 2. Include Bootstrap in Your HTML

In the `<head>` section of your `index.html`, add the Bootstrap CSS and JavaScript files along with jQuery:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cafe Website</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <a class="navbar-brand" href="#">Cafe Delight</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav ml-auto">
                <li class="nav-item active">
                    <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">Menu</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">About Us</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">Contact</a>
                </li>
            </ul>
        </div>
    </nav>

    <div class="container mt-5">
        <h1>Welcome to Cafe Delight!</h1>
        <p>Enjoy our finest selection of coffee and pastries.</p>
    </div>
</body>
</html>
```

### Explanation of the Code:

1. **Navbar Component**: 
   - The `navbar` class creates a responsive navigation bar. The `navbar-expand-lg` class makes the navbar responsive, expanding it on larger screens and collapsing it into a toggleable menu on smaller screens.
   - The `bg-light` class gives the navbar a light background.
   - The `navbar-toggler` button is used to toggle the visibility of the menu items on smaller screens.
   
2. **Navbar Items**:
   - The `navbar-nav` class is used to create a list of navigation links.
   - The `ml-auto` class is used to align the navigation items to the right.

3. **Collapse Functionality**:
   - The `collapse` class and `data-toggle` attributes are used to manage the visibility of the navigation links on smaller screens.

### 4. Add Some Basic Content

You can add some introductory text or images to your page to simulate a cafe website. Here’s an example of some additional content:

```html
<div class="container mt-5">
    <h1>Welcome to Cafe Delight!</h1>
    <p>Enjoy our finest selection of coffee and pastries.</p>
    <img src="https://via.placeholder.com/800x400" class="img-fluid" alt="Cafe Image">
</div>
```

### 5. Open Your Cafe Website in a Browser

To see your responsive navigation bar in action, open the `index.html` file in a web browser. You should see the navigation bar at the top, which collapses into a toggle button when the window is resized to a smaller width.

### Conclusion

You’ve successfully created a responsive navigation bar using Bootstrap for a cafe website. This navbar adapts to different screen sizes, providing an intuitive user experience. You can further customize it with additional styles and features, such as dropdowns, icons, or a brand logo. Enjoy building your cafe website!

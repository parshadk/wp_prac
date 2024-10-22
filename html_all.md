Sure! Here are examples for each of the requested tasks. Each example provides a basic structure and can be further customized to fit specific needs.

### 1. Basic Web Page for a Personal Blog

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Personal Blog</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Welcome to My Blog!</h1>
        <img src="profile.jpg" alt="Profile Picture" width="150">
        <nav>
            <ul>
                <li><a href="#about">About Me</a></li>
                <li><a href="#blog">Blog Posts</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <section id="about">
        <h2>About Me</h2>
        <p>Hello! I am a passionate blogger sharing my thoughts and experiences.</p>
    </section>

    <section id="blog">
        <h2>Blog Posts</h2>
        <p>Check out my latest posts!</p>
    </section>

    <section id="contact">
        <h2>Contact</h2>
        <p>Feel free to reach out!</p>
    </section>

    <footer>
        <p>&copy; 2024 My Personal Blog</p>
    </footer>
</body>
</html>
```

### 2. Personal Portfolio Webpage Using HTML5 Semantic Elements

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>My Portfolio</h1>
        <p>Welcome to my digital resume!</p>
    </header>

    <section id="experience">
        <h2>Experience</h2>
        <p>Details about my work experience.</p>
    </section>

    <section id="skills">
        <h2>Skills</h2>
        <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
        </ul>
    </section>

    <section id="projects">
        <h2>Projects</h2>
        <p>Here are some of my projects:</p>
        <ul>
            <li>Project 1</li>
            <li>Project 2</li>
            <li>Project 3</li>
        </ul>
    </section>

    <footer>
        <p>&copy; 2024 My Portfolio</p>
    </footer>
</body>
</html>
```

### 3. Product Catalog Using HTML Tables and Lists

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product Catalog</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Product Catalog</h1>
    </header>

    <table border="1">
        <thead>
            <tr>
                <th>Product</th>
                <th>Price</th>
                <th>Specifications</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Smartphone</td>
                <td>$699</td>
                <td>5G, 128GB Storage</td>
            </tr>
            <tr>
                <td>Laptop</td>
                <td>$999</td>
                <td>Intel i7, 16GB RAM</td>
            </tr>
        </tbody>
    </table>
</body>
</html>
```

### 4. Contact Form Using HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contact Us</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Contact Us</h1>
    </header>

    <form>
        <label for="name">Name:</label>
        <input type="text" id="name" required>

        <label for="email">Email:</label>
        <input type="email" id="email" required>

        <label>Service Inquiry:</label>
        <input type="radio" name="service" value="web design" id="webdesign">
        <label for="webdesign">Web Design</label>
        <input type="radio" name="service" value="graphic design" id="graphicdesign">
        <label for="graphicdesign">Graphic Design</label>

        <label for="message">Message:</label>
        <textarea id="message" required></textarea>

        <label for="contact-method">Preferred Contact Method:</label>
        <input type="checkbox" id="email-contact" value="email">
        <label for="email-contact">Email</label>
        <input type="checkbox" id="phone-contact" value="phone">
        <label for="phone-contact">Phone</label>

        <button type="submit">Submit</button>
    </form>
</body>
</html>
```

### 5. Photo Gallery Using HTML and Image Elements

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Photo Gallery</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Travel Blog Gallery</h1>
    </header>

    <section>
        <h2>Gallery</h2>
        <div>
            <img src="destination1.jpg" alt="Destination 1" width="300">
            <p>Beautiful Beach</p>
        </div>
        <div>
            <img src="destination2.jpg" alt="Destination 2" width="300">
            <p>Mountain View</p>
        </div>
        <div>
            <img src="destination3.jpg" alt="Destination 3" width="300">
            <p>City Lights</p>
        </div>
    </section>

    <footer>
        <p>&copy; 2024 Travel Blog</p>
    </footer>
</body>
</html>
```

### 6. Simple HTML Page with Internal CSS for About Us

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About Us</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            color: #333;
        }
        h1 {
            color: #2c3e50;
        }
        section {
            padding: 20px;
            background-color: white;
            margin: 20px;
            border-radius: 8px;
        }
        .mission {
            background-color: #e74c3c;
            color: white;
        }
        .values {
            background-color: #3498db;
            color: white;
        }
    </style>
</head>
<body>

    <header>
        <h1>About Us</h1>
    </header>

    <section>
        <h2>Our History</h2>
        <p>We started our journey in 2020...</p>
    </section>

    <section class="mission">
        <h2>Our Mission</h2>
        <p>To provide quality services to our customers.</p>
    </section>

    <section class="values">
        <h2>Our Values</h2>
        <p>Integrity, Quality, and Customer Satisfaction.</p>
    </section>

    <footer>
        <p>&copy; 2024 Our Company</p>
    </footer>
</body>
</html>
```

### Summary

These examples provide a foundation for building various web pages using HTML. You can expand on these by adding styles, scripts, or other functionalities as needed!

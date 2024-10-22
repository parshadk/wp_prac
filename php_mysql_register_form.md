To create a registration form using PHP that stores user data (name, email, and password) in a MySQL database, we will follow these steps:

1. **Set up the environment:**
   - Install PHP.
   - Install MySQL.
   - Configure Apache or any other web server.

2. **Create a MySQL database and table to store the user information.**

3. **Build the PHP registration form with validation.**

4. **Store the submitted form data in the MySQL database.**

### Step-by-Step Implementation

#### 1. **Set Up the MySQL Database**

First, create a MySQL database and a table to store user details. Open the MySQL shell or use a tool like phpMyAdmin and run the following SQL commands:

```sql
CREATE DATABASE membership_site;

USE membership_site;

CREATE TABLE users (
  id INT(11) AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  password VARCHAR(255) NOT NULL
);
```

This will create a `membership_site` database with a `users` table to store the `id`, `name`, `email`, and `password`.

#### 2. **Create a Registration Form (HTML)**

Create an `index.html` file for the user registration form:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Registration Form</title>
</head>
<body>
  <h2>Sign Up</h2>
  <form action="register.php" method="POST">
    <label for="name">Name:</label>
    <input type="text" name="name" required><br><br>
    
    <label for="email">Email:</label>
    <input type="email" name="email" required><br><br>
    
    <label for="password">Password:</label>
    <input type="password" name="password" required><br><br>
    
    <button type="submit">Register</button>
  </form>
</body>
</html>
```

This HTML form takes the user's name, email, and password and submits the data to `register.php`.

#### 3. **PHP Script to Handle Form Submission (register.php)**

Create a `register.php` file to handle form submissions and store the data in MySQL.

```php
<?php
// Database connection details
$host = "localhost";
$dbname = "membership_site";
$username = "root"; // replace with your MySQL username
$password = "";     // replace with your MySQL password

// Connect to MySQL
$conn = new mysqli($host, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// If form is submitted
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Capture and sanitize form inputs
    $name = $conn->real_escape_string($_POST['name']);
    $email = $conn->real_escape_string($_POST['email']);
    $password = password_hash($_POST['password'], PASSWORD_DEFAULT);  // Hash the password for security

    // Check if the email already exists
    $check_email = "SELECT * FROM users WHERE email = '$email'";
    $result = $conn->query($check_email);

    if ($result->num_rows > 0) {
        echo "This email is already registered.";
    } else {
        // Insert user data into the database
        $sql = "INSERT INTO users (name, email, password) VALUES ('$name', '$email', '$password')";

        if ($conn->query($sql) === TRUE) {
            echo "Registration successful!";
        } else {
            echo "Error: " . $sql . "<br>" . $conn->error;
        }
    }
}

// Close the connection
$conn->close();
?>
```

- **Database Connection:** The script connects to the MySQL database using `mysqli`.
- **Form Handling:** When the form is submitted (via POST), it captures the user's input and sanitizes it using `real_escape_string` to prevent SQL injection.
- **Password Hashing:** The password is hashed using `password_hash()` to store it securely.
- **Duplicate Email Check:** Before inserting a new user, the script checks if the email is already registered.
- **User Insertion:** If the email does not exist, the script inserts the user into the database.
- **Feedback:** The script returns messages indicating whether registration was successful or if there was an error.

#### 4. **Run the Application**

1. Place the `index.html` and `register.php` files in the web server's root directory (e.g., `/var/www/html` for Apache on Linux or `htdocs` for XAMPP on Windows).

2. Access the registration form via `http://localhost/index.html`.

3. Fill out the form and submit it.

If the form is successfully submitted, the user will be added to the `users` table in the `membership_site` database.



#### 6. **Conclusion**

You now have a basic user registration system in PHP that stores user details (name, email, password) in a MySQL database. You can enhance this by adding more form fields, validation, and features like user authentication, email verification, and password reset.

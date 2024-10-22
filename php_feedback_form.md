To implement a web page in PHP that displays form data submitted by users, such as a feedback form, we'll follow these steps:

1. **Create a feedback form for users to submit comments.**
2. **Store the comments in a database (optional) or display them directly.**
3. **Display the submitted comments on the same page.**

For simplicity, I'll demonstrate both scenarios:
- Directly displaying the comments without using a database.
- Using a MySQL database to store and retrieve comments.

---

### Scenario 1: Display Submitted Comments Without a Database

In this version, the comments are not stored in a database but rather displayed directly on the same page after submission.

#### 1. Create the PHP feedback form (feedback.php)

```php
<?php
// Initialize an empty array to store comments
$comments = [];

// Check if the form is submitted
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Sanitize and capture user input
    $name = htmlspecialchars($_POST['name']);
    $comment = htmlspecialchars($_POST['comment']);
    
    // Add the submitted comment to the array
    $comments[] = ['name' => $name, 'comment' => $comment];
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Feedback Form</title>
</head>
<body>
    <h1>Feedback Form</h1>
    
    <!-- Feedback form -->
    <form action="feedback.php" method="POST">
        <label for="name">Your Name:</label><br>
        <input type="text" name="name" required><br><br>
        
        <label for="comment">Your Comment:</label><br>
        <textarea name="comment" required></textarea><br><br>
        
        <button type="submit">Submit</button>
    </form>
    
    <h2>Comments:</h2>
    <ul>
        <?php foreach ($comments as $c): ?>
            <li>
                <strong><?php echo $c['name']; ?></strong>: <?php echo $c['comment']; ?>
            </li>
        <?php endforeach; ?>
    </ul>
</body>
</html>
```

#### Explanation:

- **Form Handling:** When the form is submitted, the `$_POST` array captures the data. The `htmlspecialchars()` function sanitizes the input to prevent XSS attacks.
- **Display Comments:** The comments are stored in an array and displayed in a list using a `foreach` loop.
- **Limitation:** The comments are not persistent; refreshing the page or submitting a new comment will clear the previous comments since they are not stored.

---

### Scenario 2: Store and Display Comments Using a MySQL Database

In this version, we'll store the submitted comments in a MySQL database and retrieve them for display.

#### 1. Set Up the MySQL Database

Create a MySQL database and table to store the comments.

```sql
CREATE DATABASE feedback_db;

USE feedback_db;

CREATE TABLE comments (
    id INT(11) AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    comment TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 2. Create a Database Connection Script (db.php)

This script will handle the connection to the MySQL database.

```php
<?php
// Database credentials
$host = 'localhost';
$dbname = 'feedback_db';
$username = 'root'; // Replace with your MySQL username
$password = '';     // Replace with your MySQL password

// Create a connection
$conn = new mysqli($host, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>
```

#### 3. Create the PHP Feedback Form (feedback.php)

```php
<?php
include('db.php');

// If the form is submitted
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Sanitize and capture user input
    $name = $conn->real_escape_string($_POST['name']);
    $comment = $conn->real_escape_string($_POST['comment']);
    
    // Insert the comment into the database
    $sql = "INSERT INTO comments (name, comment) VALUES ('$name', '$comment')";
    
    if ($conn->query($sql) === TRUE) {
        echo "Comment submitted successfully!";
    } else {
        echo "Error: " . $sql . "<br>" . $conn->error;
    }
}

// Fetch all comments from the database
$sql = "SELECT * FROM comments ORDER BY created_at DESC";
$result = $conn->query($sql);

$conn->close();
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Feedback Form</title>
</head>
<body>
    <h1>Feedback Form</h1>
    
    <!-- Feedback form -->
    <form action="feedback.php" method="POST">
        <label for="name">Your Name:</label><br>
        <input type="text" name="name" required><br><br>
        
        <label for="comment">Your Comment:</label><br>
        <textarea name="comment" required></textarea><br><br>
        
        <button type="submit">Submit</button>
    </form>
    
    <h2>Comments:</h2>
    <ul>
        <?php if ($result->num_rows > 0): ?>
            <?php while ($row = $result->fetch_assoc()): ?>
                <li>
                    <strong><?php echo htmlspecialchars($row['name']); ?></strong>: 
                    <?php echo htmlspecialchars($row['comment']); ?>
                    <em>(<?php echo $row['created_at']; ?>)</em>
                </li>
            <?php endwhile; ?>
        <?php else: ?>
            <li>No comments yet.</li>
        <?php endif; ?>
    </ul>
</body>
</html>
```

#### Explanation:

- **Form Handling:** When the form is submitted, the data is sanitized and inserted into the `comments` table using an SQL `INSERT` statement.
- **Display Comments:** After inserting the comment, all comments are fetched from the database and displayed in reverse chronological order (newest first).
- **Database Connection:** The `db.php` script is included to establish the database connection.
- **Persistent Comments:** The comments are stored in the MySQL database, so they persist even after refreshing the page or restarting the server.

---

### Conclusion

- **Scenario 1:** Simple and effective for small-scale applications where comment persistence is not necessary. However, comments are not saved permanently.
- **Scenario 2:** More robust as comments are stored in a MySQL database, ensuring that they persist and can be managed more efficiently. This approach is suitable for larger applications.

With either method, you now have a functional feedback form in PHP that displays submitted comments!

To create a PHP application that connects to a MySQL database and performs CRUD (Create, Read, Update, Delete) operations, we'll develop an admin panel for managing blog posts. This admin panel will allow users to:

- Add new blog posts.
- View all blog posts.
- Edit existing blog posts.
- Delete blog posts.

### Step-by-Step Guide

#### 1. **Set Up the MySQL Database**

First, create a MySQL database and a table for storing blog posts. You can use phpMyAdmin or MySQL command-line interface to create the database and table.

```sql
CREATE DATABASE blog;

USE blog;

CREATE TABLE posts (
    id INT(11) AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    author VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

This will create a `blog` database with a `posts` table to store the `id`, `title`, `content`, `author`, and `created_at` fields.

#### 2. **Create a Database Connection Script (db.php)**

Create a `db.php` file that will handle the connection to the MySQL database. All other scripts will include this file to establish the database connection.

```php
<?php
// Database credentials
$host = 'localhost';
$dbname = 'blog';
$username = 'root';  // Replace with your MySQL username
$password = '';      // Replace with your MySQL password

// Create a connection
$conn = new mysqli($host, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>
```

This script establishes a connection to the MySQL database.

#### 3. **Create the Admin Panel Layout (admin.php)**

Create an `admin.php` file that will serve as the dashboard for managing the blog posts. This page will display all the posts in the database and provide links to add, edit, or delete posts.

```php
<?php
include('db.php');

// Fetch all posts from the database
$sql = "SELECT * FROM posts";
$result = $conn->query($sql);
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Admin Panel - Manage Blog Posts</title>
</head>
<body>
    <h1>Blog Posts</h1>
    <a href="add_post.php">Add New Post</a>
    <table border="1">
        <tr>
            <th>ID</th>
            <th>Title</th>
            <th>Author</th>
            <th>Created At</th>
            <th>Actions</th>
        </tr>
        <?php if ($result->num_rows > 0): ?>
            <?php while ($row = $result->fetch_assoc()): ?>
                <tr>
                    <td><?php echo $row['id']; ?></td>
                    <td><?php echo $row['title']; ?></td>
                    <td><?php echo $row['author']; ?></td>
                    <td><?php echo $row['created_at']; ?></td>
                    <td>
                        <a href="edit_post.php?id=<?php echo $row['id']; ?>">Edit</a>
                        <a href="delete_post.php?id=<?php echo $row['id']; ?>" onclick="return confirm('Are you sure?')">Delete</a>
                    </td>
                </tr>
            <?php endwhile; ?>
        <?php else: ?>
            <tr>
                <td colspan="5">No posts found.</td>
            </tr>
        <?php endif; ?>
    </table>
</body>
</html>

<?php $conn->close(); ?>
```

This file fetches all blog posts from the database and displays them in a table. It includes links to add, edit, and delete blog posts.

#### 4. **Create the Add Post Page (add_post.php)**

Now, let's create a page that allows users to add new blog posts.

```php
<?php
include('db.php');

// If the form is submitted
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $title = $conn->real_escape_string($_POST['title']);
    $content = $conn->real_escape_string($_POST['content']);
    $author = $conn->real_escape_string($_POST['author']);

    // Insert post into database
    $sql = "INSERT INTO posts (title, content, author) VALUES ('$title', '$content', '$author')";

    if ($conn->query($sql) === TRUE) {
        echo "New post added successfully!";
    } else {
        echo "Error: " . $sql . "<br>" . $conn->error;
    }

    $conn->close();
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Add New Post</title>
</head>
<body>
    <h1>Add New Post</h1>
    <form action="add_post.php" method="POST">
        <label for="title">Title:</label><br>
        <input type="text" name="title" required><br><br>
        <label for="content">Content:</label><br>
        <textarea name="content" required></textarea><br><br>
        <label for="author">Author:</label><br>
        <input type="text" name="author"><br><br>
        <button type="submit">Submit</button>
    </form>
    <a href="admin.php">Back to Admin Panel</a>
</body>
</html>
```

This page provides a form to add a new blog post. When the form is submitted, the data is inserted into the `posts` table.

#### 5. **Create the Edit Post Page (edit_post.php)**

Next, let's create a page for editing existing posts.

```php
<?php
include('db.php');

// Get the post ID
$id = $_GET['id'];

// Fetch the post details
$sql = "SELECT * FROM posts WHERE id = $id";
$result = $conn->query($sql);
$post = $result->fetch_assoc();

// If the form is submitted
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $title = $conn->real_escape_string($_POST['title']);
    $content = $conn->real_escape_string($_POST['content']);
    $author = $conn->real_escape_string($_POST['author']);

    // Update the post
    $sql = "UPDATE posts SET title='$title', content='$content', author='$author' WHERE id=$id";

    if ($conn->query($sql) === TRUE) {
        echo "Post updated successfully!";
    } else {
        echo "Error: " . $sql . "<br>" . $conn->error;
    }

    $conn->close();
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Edit Post</title>
</head>
<body>
    <h1>Edit Post</h1>
    <form action="edit_post.php?id=<?php echo $id; ?>" method="POST">
        <label for="title">Title:</label><br>
        <input type="text" name="title" value="<?php echo $post['title']; ?>" required><br><br>
        <label for="content">Content:</label><br>
        <textarea name="content" required><?php echo $post['content']; ?></textarea><br><br>
        <label for="author">Author:</label><br>
        <input type="text" name="author" value="<?php echo $post['author']; ?>"><br><br>
        <button type="submit">Update</button>
    </form>
    <a href="admin.php">Back to Admin Panel</a>
</body>
</html>
```

This page retrieves the post data based on its ID and displays it in a form for editing. When the form is submitted, the post is updated in the database.

#### 6. **Create the Delete Post Page (delete_post.php)**

Finally, let's create a script to delete posts.

```php
<?php
include('db.php');

// Get the post ID
$id = $_GET['id'];

// Delete the post
$sql = "DELETE FROM posts WHERE id = $id";

if ($conn->query($sql) === TRUE) {
    echo "Post deleted successfully!";
} else {
    echo "Error: " . $sql . "<br>" . $conn->error;
}

$conn->close();

// Redirect back to the admin panel
header("Location: admin.php");
exit();
?>
```

This script deletes the post from the database based on its ID and then redirects back to the admin panel.

#### 7. **Testing the Application**

Now, you can test the admin panel:

1. Access the admin panel at `http://localhost/admin.php`.
2. Add new posts using `add_post.php`.
3. Edit existing posts using `edit_post.php`.
4. Delete posts using `delete_post.php`.

#### 8. **Conclusion**

You now have a fully functional PHP application that connects to a MySQL database and performs CRUD operations for managing blog posts. You can extend this admin panel by adding features like user authentication, pagination, and more advanced security practices.

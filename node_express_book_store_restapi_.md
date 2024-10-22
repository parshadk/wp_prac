To create a REST API with Node.js and Express for managing products in a bookstore, we will implement basic CRUD (Create, Read, Update, Delete) operations for books. The books' information will be stored in a MongoDB database, and we will use Mongoose to interact with the database.

### Step-by-Step Guide

#### Prerequisites
- Install Node.js and npm (Node Package Manager).
- Set up MongoDB locally or use a cloud-based solution like MongoDB Atlas.

#### 1. **Set Up the Node.js Project**

First, initialize a new Node.js project and install the necessary dependencies.

```bash
mkdir bookstore-api
cd bookstore-api
npm init -y
npm install express mongoose body-parser
```

- `express`: Web framework for Node.js.
- `mongoose`: ODM (Object Data Modeling) library for MongoDB.
- `body-parser`: Middleware for parsing incoming request bodies.

#### 2. **Create the Express Application**

Create a new file `app.js` to define the core of your Express application.

```js
const express = require('express');
const mongoose = require('mongoose');
const bodyParser = require('body-parser');

const app = express();
const port = 3000;

// Middleware
app.use(bodyParser.json());

// Connect to MongoDB (update with your MongoDB URI)
mongoose.connect('mongodb://localhost:27017/bookstore', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
}).then(() => {
  console.log("Connected to MongoDB");
}).catch((err) => {
  console.error("Error connecting to MongoDB", err);
});

// Start the server
app.listen(port, () => {
  console.log(`Server is running on http://localhost:${port}`);
});
```

This sets up an Express server and connects to a MongoDB database (`bookstore`). Update the MongoDB connection URI as needed.

#### 3. **Define the Book Model**

Create a `models` directory and a `Book.js` file inside it to define the Mongoose schema for books.

```js
// models/Book.js
const mongoose = require('mongoose');

const bookSchema = new mongoose.Schema({
  title: {
    type: String,
    required: true,
  },
  author: {
    type: String,
    required: true,
  },
  description: {
    type: String,
  },
  price: {
    type: Number,
    required: true,
  },
  publishedDate: {
    type: Date,
    default: Date.now,
  },
});

const Book = mongoose.model('Book', bookSchema);

module.exports = Book;
```

This schema defines a `Book` model with properties like `title`, `author`, `description`, `price`, and `publishedDate`.

#### 4. **Create Routes for CRUD Operations**

Create a `routes` directory and a `bookRoutes.js` file to handle the API routes.

```js
// routes/bookRoutes.js
const express = require('express');
const Book = require('../models/Book');

const router = express.Router();

// Create a new book
router.post('/books', async (req, res) => {
  try {
    const book = new Book(req.body);
    await book.save();
    res.status(201).json(book);
  } catch (err) {
    res.status(400).json({ error: err.message });
  }
});

// Get all books
router.get('/books', async (req, res) => {
  try {
    const books = await Book.find();
    res.json(books);
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

// Get a book by ID
router.get('/books/:id', async (req, res) => {
  try {
    const book = await Book.findById(req.params.id);
    if (!book) {
      return res.status(404).json({ error: 'Book not found' });
    }
    res.json(book);
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

// Update a book by ID
router.put('/books/:id', async (req, res) => {
  try {
    const book = await Book.findByIdAndUpdate(req.params.id, req.body, { new: true, runValidators: true });
    if (!book) {
      return res.status(404).json({ error: 'Book not found' });
    }
    res.json(book);
  } catch (err) {
    res.status(400).json({ error: err.message });
  }
});

// Delete a book by ID
router.delete('/books/:id', async (req, res) => {
  try {
    const book = await Book.findByIdAndDelete(req.params.id);
    if (!book) {
      return res.status(404).json({ error: 'Book not found' });
    }
    res.json({ message: 'Book deleted' });
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

module.exports = router;
```

This file defines routes for:
- **POST** `/books`: To create a new book.
- **GET** `/books`: To retrieve all books.
- **GET** `/books/:id`: To retrieve a single book by ID.
- **PUT** `/books/:id`: To update a book by ID.
- **DELETE** `/books/:id`: To delete a book by ID.

#### 5. **Connect the Routes to the Express App**

In `app.js`, connect the routes to the Express application:

```js
const bookRoutes = require('./routes/bookRoutes');

// Use the book routes
app.use('/api', bookRoutes);
```

This ensures that the `/api/books` route prefix is used for all book-related routes.

#### 6. **Run the Application**

Start the application by running:

```bash
node app.js
```

This will start the server at `http://localhost:3000`.

#### 7. **Testing the API**

You can use Postman or `curl` to test the API.

##### 1. **Create a New Book**

Send a POST request to `http://localhost:3000/api/books` with the following JSON body:

```json
{
  "title": "The Great Gatsby",
  "author": "F. Scott Fitzgerald",
  "description": "A classic novel set in the 1920s.",
  "price": 10.99
}
```

##### 2. **Retrieve All Books**

Send a GET request to `http://localhost:3000/api/books`. You should see a list of books, including the one you just created.

##### 3. **Retrieve a Single Book**

Send a GET request to `http://localhost:3000/api/books/:id` where `:id` is the ID of the book you want to retrieve.

##### 4. **Update a Book**

Send a PUT request to `http://localhost:3000/api/books/:id` with the updated book data in the request body.

##### 5. **Delete a Book**

Send a DELETE request to `http://localhost:3000/api/books/:id` where `:id` is the ID of the book you want to delete.

#### 8. **Conclusion**

You now have a REST API for managing books in a bookstore, with the ability to:
- Create new book records.
- Retrieve all book records.
- Retrieve a specific book by its ID.
- Update a book's details.
- Delete a book from the database.

You can extend this API by adding features like pagination, search functionality, and authentication (e.g., using JWT tokens) for securing endpoints.

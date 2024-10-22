To create a contact form in React with input validation using JavaScript, we will:

1. **Set up a form with fields like name, email, and message.**
2. **Validate the inputs (e.g., check if the email is valid and if mandatory fields are filled).**
3. **Display appropriate error messages when validation fails.**

### Step-by-Step Guide

### 1. Set Up the React Project

First, create a new React project if you haven't already:

```bash
npx create-react-app contact-form
cd contact-form
npm start
```

### 2. Create the Contact Form Component

In the `src` folder, open `App.js` and replace its content with the following code:

```jsx
import React, { useState } from 'react';

const App = () => {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    message: ''
  });

  const [errors, setErrors] = useState({
    name: '',
    email: '',
    message: ''
  });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData({
      ...formData,
      [name]: value
    });
  };

  const validate = () => {
    let isValid = true;
    const newErrors = { name: '', email: '', message: '' };

    // Check if name is empty
    if (formData.name.trim() === '') {
      newErrors.name = 'Name is required';
      isValid = false;
    }

    // Check if email is valid
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (formData.email.trim() === '') {
      newErrors.email = 'Email is required';
      isValid = false;
    } else if (!emailRegex.test(formData.email)) {
      newErrors.email = 'Please enter a valid email address';
      isValid = false;
    }

    // Check if message is empty
    if (formData.message.trim() === '') {
      newErrors.message = 'Message is required';
      isValid = false;
    }

    setErrors(newErrors);
    return isValid;
  };

  const handleSubmit = (e) => {
    e.preventDefault();

    if (validate()) {
      // If form is valid, submit the form
      alert('Form submitted successfully!');
      // Here, you can also handle sending form data to a backend or email service

      // Reset form fields
      setFormData({
        name: '',
        email: '',
        message: ''
      });

      // Clear error messages
      setErrors({
        name: '',
        email: '',
        message: ''
      });
    }
  };

  return (
    <div className="App">
      <h1>Contact Us</h1>
      <form onSubmit={handleSubmit}>
        {/* Name Field */}
        <div>
          <label htmlFor="name">Name:</label>
          <input
            type="text"
            id="name"
            name="name"
            value={formData.name}
            onChange={handleChange}
          />
          {errors.name && <p style={{ color: 'red' }}>{errors.name}</p>}
        </div>

        {/* Email Field */}
        <div>
          <label htmlFor="email">Email:</label>
          <input
            type="email"
            id="email"
            name="email"
            value={formData.email}
            onChange={handleChange}
          />
          {errors.email && <p style={{ color: 'red' }}>{errors.email}</p>}
        </div>

        {/* Message Field */}
        <div>
          <label htmlFor="message">Message:</label>
          <textarea
            id="message"
            name="message"
            value={formData.message}
            onChange={handleChange}
          ></textarea>
          {errors.message && <p style={{ color: 'red' }}>{errors.message}</p>}
        </div>

        {/* Submit Button */}
        <button type="submit">Submit</button>
      </form>
    </div>
  );
};

export default App;
```

### Explanation:

1. **State Management:**
   - `formData`: Holds the values for the form fields (`name`, `email`, `message`).
   - `errors`: Holds the error messages for each form field.

2. **handleChange Function:**
   - Updates the corresponding form field value when the user types into the form.

3. **validate Function:**
   - Checks the validity of the input fields:
     - Ensures the `name` and `message` fields are not empty.
     - Uses a regular expression to validate the email format.
   - Sets error messages in the `errors` state if validation fails.

4. **handleSubmit Function:**
   - Prevents the default form submission behavior.
   - Validates the form inputs, and if they are valid, submits the form (in this case, we simply display an alert).
   - Resets the form and errors after successful submission.

### 3. Add Basic Styling (Optional)

You can add some basic CSS to style the form. Create a `styles.css` file in the `src` folder and link it in `App.js`.

`src/styles.css`:

```css
.App {
  text-align: center;
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
}

form {
  display: flex;
  flex-direction: column;
}

input, textarea {
  padding: 10px;
  margin: 10px 0;
  font-size: 16px;
  width: 100%;
}

button {
  padding: 10px;
  background-color: #28a745;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #218838;
}

p {
  margin: 5px 0;
}
```

Now, import the CSS file in `App.js`:

```jsx
import './styles.css';
```

### 4. Run the Application

To start the application, run:

```bash
npm start
```

You should now see a functional contact form with client-side validation. If any required field is left blank or an invalid email is entered, appropriate error messages will be displayed.

---

### Conclusion

You have created a basic contact form in React with input validation. The form checks for:
- A non-empty `name` and `message`.
- A valid email address format.

This form can be easily extended or modified to include additional fields and more complex validation rules. You can also add features such as submitting the form data to a backend service or API for further processing.

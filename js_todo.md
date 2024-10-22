Creating a to-do list web application is a great way to practice using JavaScript for dynamic web functionality. Below is a complete example that allows users to add tasks, mark them as completed, and remove them from the list.

### Step-by-Step Guide

### 1. Set Up the Project

Create a new HTML file named `todo-list.html` and open it in your favorite code editor.

### 2. Basic HTML Structure

Add the following HTML structure for the to-do list application.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List App</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4; /* Light background */
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 600px;
            margin: auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        h2 {
            text-align: center;
        }

        #taskInput {
            width: calc(100% - 60px);
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        button {
            padding: 10px 15px;
            background-color: #28a745; /* Green */
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        button:hover {
            background-color: #218838; /* Darker green */
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            border-bottom: 1px solid #ccc;
        }

        .completed {
            text-decoration: line-through; /* Strikethrough for completed tasks */
            color: gray;
        }

        .remove {
            color: red;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>To-Do List</h2>
        <div>
            <input type="text" id="taskInput" placeholder="Add a new task...">
            <button onclick="addTask()">Add Task</button>
        </div>
        <ul id="taskList"></ul>
    </div>

    <script>
        function addTask() {
            const taskInput = document.getElementById("taskInput");
            const taskValue = taskInput.value.trim();

            if (taskValue === "") {
                alert("Please enter a task.");
                return;
            }

            const taskList = document.getElementById("taskList");
            const li = document.createElement("li");

            li.innerHTML = `
                <span>${taskValue}</span>
                <span class="remove" onclick="removeTask(this)">Remove</span>
            `;

            li.addEventListener("click", function() {
                this.classList.toggle("completed");
            });

            taskList.appendChild(li);
            taskInput.value = ""; // Clear input field
        }

        function removeTask(taskElement) {
            const taskList = document.getElementById("taskList");
            taskList.removeChild(taskElement.parentElement); // Remove the task
        }
    </script>
</body>
</html>
```

### Explanation of the Code:

1. **HTML Structure**:
   - The application contains an input field where users can type in their tasks, a button to add the task, and an unordered list (`<ul>`) to display the tasks.

2. **CSS Styles**:
   - Basic styles create a clean layout for the to-do list and improve the visibility of tasks.
   - Completed tasks have a strikethrough effect to indicate they are done.

3. **JavaScript Functionality**:
   - **`addTask()`**: This function retrieves the value from the input field. If the input is empty, it alerts the user to enter a task. If a task is entered, it creates a new list item (`<li>`) and adds it to the task list. Each task has a "Remove" span that, when clicked, calls the `removeTask()` function.
   - **Task Completion**: Each task item can be clicked to toggle the "completed" class, which applies a strikethrough style to indicate completion.
   - **`removeTask(taskElement)`**: This function removes the selected task from the list.

### 3. Test Your To-Do List Application

Open the `todo-list.html` file in a web browser. You should be able to:
- Add new tasks to the list.
- Click on tasks to mark them as completed (strikethrough).
- Click "Remove" to delete tasks from the list.

### Conclusion

You've successfully created a functional to-do list web application using JavaScript. This simple app provides a solid foundation for further enhancements, such as storing tasks in local storage, adding due dates, or filtering tasks based on their status. Enjoy building and expanding your to-do list application!

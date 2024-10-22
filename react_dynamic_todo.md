To create a dynamic to-do list application in React, we’ll build a task management app that allows users to:

1. **Add new tasks.**
2. **Set deadlines for tasks.**
3. **Mark tasks as complete.**
4. **Delete tasks.**

### Step-by-Step Guide

### 1. Set Up the React Project

First, create a React project using `create-react-app`:

```bash
npx create-react-app todo-app
cd todo-app
npm start
```

This will create the project structure and start the development server.

### 2. Create the To-Do List Component

In the `src` folder, open `App.js` and replace its content with the following code to define the to-do list logic and user interface.

```jsx
import React, { useState } from 'react';
import './App.css';

const App = () => {
  // State for managing tasks
  const [tasks, setTasks] = useState([]);
  const [newTask, setNewTask] = useState('');
  const [newDeadline, setNewDeadline] = useState('');
  
  // Add a new task
  const addTask = () => {
    if (newTask.trim() === '' || newDeadline === '') {
      alert("Please enter a task and a deadline");
      return;
    }

    const task = {
      id: Date.now(), // Unique ID for each task
      text: newTask,
      deadline: newDeadline,
      completed: false,
    };
    
    setTasks([...tasks, task]);
    setNewTask(''); // Clear the task input field
    setNewDeadline(''); // Clear the deadline input field
  };

  // Mark task as complete
  const toggleComplete = (taskId) => {
    setTasks(
      tasks.map(task =>
        task.id === taskId ? { ...task, completed: !task.completed } : task
      )
    );
  };

  // Delete task
  const deleteTask = (taskId) => {
    setTasks(tasks.filter(task => task.id !== taskId));
  };

  return (
    <div className="App">
      <h1>To-Do List</h1>
      
      {/* Input for adding new tasks */}
      <div className="add-task">
        <input
          type="text"
          placeholder="Enter task"
          value={newTask}
          onChange={(e) => setNewTask(e.target.value)}
        />
        <input
          type="date"
          value={newDeadline}
          onChange={(e) => setNewDeadline(e.target.value)}
        />
        <button onClick={addTask}>Add Task</button>
      </div>

      {/* Task list */}
      <ul>
        {tasks.map(task => (
          <li key={task.id} className={task.completed ? 'completed' : ''}>
            <span>{task.text} (Deadline: {task.deadline})</span>
            <button onClick={() => toggleComplete(task.id)}>
              {task.completed ? 'Undo' : 'Complete'}
            </button>
            <button onClick={() => deleteTask(task.id)}>Delete</button>
          </li>
        ))}
      </ul>
    </div>
  );
};

export default App;
```

### 3. Explanation

1. **State Management:**
   - `tasks`: An array that holds the list of tasks. Each task has an `id`, `text`, `deadline`, and `completed` flag.
   - `newTask`: Holds the current input value for a new task.
   - `newDeadline`: Holds the deadline input for the new task.

2. **Adding a Task:**
   - The `addTask` function creates a new task object and appends it to the `tasks` array. It ensures that both the task and deadline are provided before adding the task.

3. **Mark Task as Complete:**
   - The `toggleComplete` function toggles the `completed` status of a task.

4. **Deleting a Task:**
   - The `deleteTask` function removes the task from the list based on its unique `id`.

### 4. Add Basic Styling (Optional)

Add some CSS to style the to-do list. Create a `styles.css` file in the `src` folder and link it in `App.js`:

`src/App.css`:

```css
.App {
  text-align: center;
  padding: 20px;
}

.add-task {
  margin-bottom: 20px;
}

.add-task input {
  margin: 10px;
  padding: 10px;
  font-size: 16px;
}

.add-task button {
  padding: 10px 20px;
  background-color: #28a745;
  color: white;
  border: none;
  cursor: pointer;
}

.add-task button:hover {
  background-color: #218838;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ddd;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li.completed {
  text-decoration: line-through;
  color: gray;
}

button {
  padding: 5px 10px;
  margin-left: 10px;
}

button:hover {
  background-color: #ddd;
}
```

### 5. Run the Application

To start the application, run:

```bash
npm start
```

You should see a functional to-do list application where you can:
- **Add new tasks** with a deadline.
- **Mark tasks as complete** or undo the completion.
- **Delete tasks** from the list.

### 6. Optional Enhancements

You can add the following features to further improve the application:
- **LocalStorage**: Store tasks in the browser so that they persist after a page refresh.
- **Task Prioritization**: Add a priority level for each task.
- **Task Editing**: Allow users to edit tasks after adding them.

### Example with LocalStorage

To persist tasks between page reloads, you can modify the `useState` to load tasks from `localStorage` and store tasks when they change:

```jsx
// Inside App component
useEffect(() => {
  const storedTasks = JSON.parse(localStorage.getItem('tasks'));
  if (storedTasks) {
    setTasks(storedTasks);
  }
}, []);

useEffect(() => {
  localStorage.setItem('tasks', JSON.stringify(tasks));
}, [tasks]);
```

This will load the tasks from `localStorage` when the component first mounts, and save the tasks to `localStorage` every time the `tasks` array changes.

---

### Conclusion

You’ve created a dynamic to-do list app using React where users can:
- Add tasks with deadlines.
- Mark tasks as complete.
- Delete tasks.

This basic app can be extended with features like local persistence, priority settings, and task editing to make it even more functional!

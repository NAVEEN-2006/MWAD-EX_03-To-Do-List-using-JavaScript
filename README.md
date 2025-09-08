# MWAD-EX_03-To-Do-List-using-JavaScript
## Date: 08-09-2025

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
### index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>To-Do App</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="todo-container">
    <h1>My To-Do List</h1>
    <div class="input-section">
      <input type="text" id="taskInput" placeholder="Enter a new task...">
      <button id="addBtn">Add</button>
    </div>
    <ul id="taskList"></ul>
  </div>

  <!-- Footer Section -->
  <footer>
    <p>Developed by: <b>NAVEEN KUMAR S</b> | Reg No: <b>212223040129</b></p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
```

### style.css
```
body {
  font-family: Arial, sans-serif;
  background: #f4f4f9;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  padding-bottom: 50px; 
}

.todo-container {
  background: #fff;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  width: 350px;
}

h1 {
  text-align: center;
  color: #333;
}

.input-section {
  display: flex;
  margin-bottom: 15px;
}

#taskInput {
  flex: 1;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 8px 0 0 8px;
  outline: none;
}

#addBtn {
  padding: 10px 20px;
  border: none;
  background: #28a745;
  color: white;
  font-weight: bold;
  border-radius: 0 8px 8px 0;
  cursor: pointer;
}

#addBtn:hover {
  background: #218838;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  padding: 10px;
  margin: 5px 0;
  background: #f9f9f9;
  border-radius: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li.completed {
  text-decoration: line-through;
  color: gray;
}

button.delete {
  background: red;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 6px;
  cursor: pointer;
}

button.delete:hover {
  background: darkred;
}

footer {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  text-align: center;
  background: #f1f1f1;
  padding: 10px;
  color: #555;
  font-size: 14px;
  border-top: 1px solid #ccc;
}
```

### script.js
```
const taskInput = document.getElementById("taskInput");
const addBtn = document.getElementById("addBtn");
const taskList = document.getElementById("taskList");

window.onload = loadTasks;

addBtn.addEventListener("click", addTask);

function addTask() {
  const taskText = taskInput.value.trim();

  if (taskText === "") {
    alert("Please enter a task!");
    return;
  }

  createTaskElement(taskText);
  saveTask(taskText);

  taskInput.value = "";
}

function createTaskElement(taskText, completed = false) {
  const li = document.createElement("li");
  if (completed) li.classList.add("completed");

  li.textContent = taskText;

  li.addEventListener("click", () => {
    li.classList.toggle("completed");
    updateLocalStorage();
  });

  const delBtn = document.createElement("button");
  delBtn.textContent = "X";
  delBtn.classList.add("delete");
  delBtn.addEventListener("click", () => {
    li.remove();
    updateLocalStorage();
  });

  li.appendChild(delBtn);
  taskList.appendChild(li);
}

function saveTask(taskText) {
  let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
  tasks.push({ text: taskText, completed: false });
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

function loadTasks() {
  let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
  tasks.forEach(task => {
    createTaskElement(task.text, task.completed);
  });
}

function updateLocalStorage() {
  const tasks = [];
  document.querySelectorAll("li").forEach(li => {
    tasks.push({
      text: li.firstChild.textContent,
      completed: li.classList.contains("completed")
    });
  });
  localStorage.setItem("tasks", JSON.stringify(tasks));
}
```


## OUTPUT
<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/3e805254-a445-46b6-b9b1-82bd6fa1ea0b" />




## RESULT
The program for creating To-do list using JavaScript is executed successfully.

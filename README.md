<!DOCTYPE html>
<html>
<head>
  <title>To-Do List</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <h1>My To-Do List</h1>

  <div>
    <input type="text" id="taskInput" placeholder="Add a new task">
    <button onclick="addTask()">Add</button>
  </div>

  <ul id="taskList">
    <!-- Tasks will be added dynamically here -->
  </ul>

  <script src="script.js"></script>
</body>
</html>
/* You can add your own CSS styles here */
let tasks = [];

function displayTasks() {
  const taskList = document.getElementById("taskList");
  taskList.innerHTML = "";
  
  tasks.forEach((task, index) => {
    const li = document.createElement("li");
    li.innerHTML = `
      <span>${task}</span>
      <button onclick="editTask(${index})">Edit</button>
      <button onclick="deleteTask(${index})">Delete</button>
    `;
    taskList.appendChild(li);
  });
}

function addTask() {
  const taskInput = document.getElementById("taskInput");
  const task = taskInput.value.trim();

  if (task !== "") {
    tasks.push(task);
    displayTasks();
    taskInput.value = "";
  } else {
    alert("Please enter a task!");
  }
}

function editTask(index) {
  const newTask = prompt("Edit task:", tasks[index]);

  if (newTask !== null) {
    tasks[index] = newTask.trim();
    displayTasks();
  }
}

function deleteTask(index) {
  tasks.splice(index, 1);
  displayTasks();
}

window.onload = function () {
  displayTasks();
};

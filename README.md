# Final Project and Deployment

## Objectives
Build a fully functional web application.
🔹 1. index.html
html
Copy
Edit
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Task Tracker</title>
  <link rel="stylesheet" href="style.css"/>
</head>
<body>
  <div class="container">
    <h1>Task Tracker ✅</h1>
    <input type="text" id="taskInput" placeholder="Add a new task...">
    <button onclick="addTask()">Add Task</button>
    <ul id="taskList"></ul>
  </div>
  <script src="script.js"></script>
</body>
</html>
🔹 2. style.css
css
Copy
Edit
body {
  font-family: Arial, sans-serif;
  padding: 20px;
  background: #f0f2f5;
}
.container {
  max-width: 400px;
  margin: auto;
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}
input {
  width: 70%;
  padding: 10px;
  margin-right: 5px;
}
button {
  padding: 10px;
}
li {
  list-style: none;
  margin-top: 10px;
}
.completed {
  text-decoration: line-through;
  color: gray;
}
🔹 3. script.js
javascript
Copy
Edit
document.addEventListener('DOMContentLoaded', loadTasks);

function addTask() {
  const input = document.getElementById('taskInput');
  const taskText = input.value.trim();
  if (!taskText) return;

  const taskList = document.getElementById('taskList');
  const li = document.createElement('li');
  li.textContent = taskText;
  li.addEventListener('click', () => {
    li.classList.toggle('completed');
    saveTasks();
  });
  li.addEventListener('contextmenu', (e) => {
    e.preventDefault();
    li.remove();
    saveTasks();
  });

  taskList.appendChild(li);
  input.value = '';
  saveTasks();
}

function saveTasks() {
  const tasks = [];
  document.querySelectorAll('#taskList li').forEach(li => {
    tasks.push({ text: li.textContent, completed: li.classList.contains('completed') });
  });
  localStorage.setItem('tasks', JSON.stringify(tasks));
}

function loadTasks() {
  const tasks = JSON.parse(localStorage.getItem('tasks')) || [];
  tasks.forEach(task => {
    const li = document.createElement('li');
    li.textContent = task.text;
    if (task.completed) li.classList.add('completed');
    li.addEventListener('click', () => {
      li.classList.toggle('completed');
      saveTasks();
    });
    li.addEventListener('contextmenu', (e) => {
      e.preventDefault();
      li.remove();
      saveTasks();
    });
    document.getElementById('taskList').appendChild(li);
  });
}
Apply HTML, CSS, and JavaScript concepts learned.
1. HTML (Structure)
html
Copy
Edit
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Tip Calculator</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <h1>Tip Calculator 💰</h1>
    <label for="bill">Bill Amount:</label>
    <input type="number" id="bill" placeholder="Enter bill amount" />

    <label for="tip">Tip Percentage:</label>
    <input type="number" id="tip" placeholder="Enter tip %" />

    <button onclick="calculateTip()">Calculate</button>

    <div class="result" id="result"></div>
  </div>

  <script src="script.js"></script>
</body>
</html>
2. CSS (Styling)
css
Copy
Edit
body {
  font-family: Arial, sans-serif;
  background: #f4f4f4;
  padding: 40px;
  display: flex;
  justify-content: center;
}

.container {
  background: white;
  padding: 30px;
  border-radius: 10px;
  width: 300px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

input {
  width: 100%;
  margin-bottom: 15px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

button {
  width: 100%;
  padding: 10px;
  background: #2d89ef;
  color: white;
  border: none;
  border-radius: 5px;
  font-size: 16px;
}

.result {
  margin-top: 20px;
  font-weight: bold;
  color: #333;
}
3. JavaScript (Logic)
javascript
Copy
Edit
function calculateTip() {
  const bill = parseFloat(document.getElementById('bill').value);
  const tipPercent = parseFloat(document.getElementById('tip').value);

  if (isNaN(bill) || isNaN(tipPercent)) {
    document.getElementById('result').textContent = "Please enter valid numbers.";
    return;
  }

  const tipAmount = bill * (tipPercent / 100);
  const total = bill + tipAmount;

  document.getElementById('result').innerHTML = `
    Tip: $${tipAmount.toFixed(2)} <br>
    Total: $${total.toFixed(2)}
  `;
}

Deploy the project using GitHub Pages, Netlify, or Vercel.
🚀 Option 1: Deploy with GitHub Pages
✅ Best for: Static sites (HTML, CSS, JS only)
📝 Steps:
Create a GitHub repository

Go to github.com

Click New Repository

Name it (e.g., tip-calculator) and click Create Repository

Upload your files

Upload your index.html, style.css, and script.js manually

Or use Git from your computer:

bash
Copy
Edit
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/your-username/tip-calculator.git
git push -u origin main
Enable GitHub Pages

Go to your repo’s Settings

Scroll to Pages

Under Source, choose main branch and /root directory

Click Save

Access your site

After a few moments, your site will be live at:
https://your-username.github.io/tip-calculator

🚀 Option 2: Deploy with Netlify
✅ Best for: Easy drag-and-drop or Git-based deployment
📝 Steps:
Go to netlify.com and sign up/login

Choose "Add new site" > "Deploy manually"

Drag and drop your project folder (with index.html) onto the upload box

Netlify will deploy the site instantly

You’ll get a live URL like:
https://your-project-name.netlify.app

💡 You can connect a GitHub repo for continuous deployment as well.

🚀 Option 3: Deploy with Vercel
✅ Best for: Jamstack or frontend frameworks (Next.js, React) but works with static sites too
📝 Steps:
Go to vercel.com and sign in with GitHub

Click "Add New Project"

Select your GitHub repo (e.g., tip-calculator)

Keep all default settings and click Deploy

Once deployed, your project will be live at something like:
https://tip-calculator.vercel.app


## Instructions
Choose one of the following project ideas:
Blog Website: Implement a multi-page site with navigation.
Ecommerce Website: Implement a multi-page site with navigation.

>[!NOTE]
> - Include at least:
> - A responsive design.
> - JavaScript interactivity.
> - A deployment link.

## Tasks

Create a well-structured HTML5 document.
Use at least 5 different HTML elements.
Ensure semantic correctness.

Good luck and happy coding! 🚀💻

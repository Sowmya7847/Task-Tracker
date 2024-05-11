<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Task Tracker</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(to right, #4A69BD, #663399);
      color: #fff;
      margin: 0;
      padding: 0;
    }

    .container {
      max-width: 800px;
      margin: 40px auto;
      padding: 20px;
    }

    h1 {
      text-align: center;
      margin-bottom: 30px;
    }

    #taskInput {
      padding: 10px;
      font-size: 16px;
      border: none;
      border-radius: 5px;
      width: 60%;
      margin-right: 10px;
    }

    #addTask {
      padding: 10px 20px;
      font-size: 16px;
      background-color: #663399;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    #taskList {
      list-style-type: none;
      padding: 0;
    }

    #taskList li {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background-color: #4A69BD;
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 5px;
    }

    #taskList li.completed {
      text-decoration: line-through;
      color: #ccc;
    }

    .points-container {
      display: flex;
      justify-content: center;
      margin-top: 20px;
      font-size: 18px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Task Tracker</h1>
    <input type="text" id="taskInput" placeholder="Add a new task">
    <button id="addTask">Add Task</button>
    <ul id="taskList"></ul>
    <div class="points-container">
      Points: <span id="pointsDisplay">0</span>
    </div>
  </div>
  <script>
    let points = 0;
    const pointsDisplay = document.getElementById('pointsDisplay');

    document.getElementById('addTask').addEventListener('click', function() {
      let taskInput = document.getElementById('taskInput');
      let taskList = document.getElementById('taskList');

      if (taskInput.value.trim() !== '') {
        let taskItem = document.createElement('li');
        taskItem.textContent = taskInput.value;
        taskList.appendChild(taskItem);
        taskInput.value = '';

        let completeButton = document.createElement('button');
        completeButton.textContent = 'Complete';
        completeButton.addEventListener('click', function() {
          taskItem.classList.toggle('completed');
          if (taskItem.classList.contains('completed')) {
            points += 10;
            pointsDisplay.textContent = points;
          } else {
            points -= 10;
            pointsDisplay.textContent = points;
          }
        });
        taskItem.appendChild(completeButton);
      }
    });
  </script>
</body>
</html>

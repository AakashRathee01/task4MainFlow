# task4MainFlow<
<-- html code (index.html) -->

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>To-Do List 📝</h1>
        <div class="input-container">
            <input type="text" id="todo-input" placeholder="Add your task">
            <button id="add-button">Add</button>
        </div>
        <ul id="todo-list"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>



<-- CSS code(style.css) -->

body {
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #4b6cb7, #182848);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background: white;
    padding: 40px;
    border-radius: 20px;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
    width: 100%;
    max-width: 450px;
    text-align: center;
}

h1 {
    margin: 0 0 20px 0;
    font-size: 28px;
    color: #333;
}

.input-container {
    display: flex;
    justify-content: space-between;
    gap: 10px;
}

#todo-input {
    flex-grow: 1;
    padding: 15px;
    border: 1px solid #ccc;
    border-radius: 50px;
    font-size: 16px;
}

#add-button {
    background-color: #ff7f50;
    color: white;
    border: none;
    border-radius: 50px;
    cursor: pointer;
    padding: 15px 20px;
    font-size: 16px;
}

#add-button:hover {
    background-color: #ff6347;
}

ul {
    list-style-type: none;
    padding: 0;
    margin: 20px 0 0 0;
}

li {
    background: #f7f7f7;
    margin: 10px 0;
    padding: 15px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-radius: 50px;
    font-size: 16px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

li .delete-button {
    background: none;
    border: none;
    color: #dc3545;
    font-size: 20px;
    cursor: pointer;
    padding: 5px 10px;
    border-radius: 50%;
}

li .delete-button:hover {
    color: #c82333;
}

li .done-checkbox {
    margin-right: 10px;
    transform: scale(1.5);
}



<-- JavaScript (script.js) -->

document.getElementById('add-button').addEventListener('click', function() {
    const todoInput = document.getElementById('todo-input');
    const todoText = todoInput.value.trim();
    
    if (todoText !== "") {
        addTodoItem(todoText);
        todoInput.value = "";
    }
});

function addTodoItem(todoText) {
    const todoList = document.getElementById('todo-list');
    const li = document.createElement('li');

    const checkbox = document.createElement('input');
    checkbox.type = 'checkbox';
    checkbox.className = 'done-checkbox';
    checkbox.addEventListener('change', function() {
        if (checkbox.checked) {
            li.style.textDecoration = "line-through";
        } else {
            li.style.textDecoration = "none";
        }
    });

    li.appendChild(checkbox);
    li.appendChild(document.createTextNode(todoText));

    const deleteButton = document.createElement('button');
    deleteButton.textContent = "×";
    deleteButton.className = "delete-button";
    deleteButton.addEventListener('click', function() {
        todoList.removeChild(li);
    });
    
    li.appendChild(deleteButton);
    todoList.appendChild(li);
}

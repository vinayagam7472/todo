# To-Do List Web App

## Live Demo
https://vinayagam7472.github.io/todo/todo/

## Overview
This is a simple To-Do List application built using HTML, CSS, and JavaScript.
It allows users to add, edit, delete, and mark tasks as completed.

---

## Features
- Add tasks
- Edit tasks
- Delete tasks
- Mark tasks as completed

---

## Technologies Used
- HTML
- CSS
- JavaScript

---

## How the Script Works (Detailed Explanation)

### 1. Creating an Array
```javascript
let list = [];
```
This array is used to store all the task values entered by the user.

---

### 2. addtask() Function
```javascript
function addtask() {
```
This function is called when the user clicks the "add" button.

---

### 3. Getting Input Value
```javascript
let inputBox = document.getElementById("inputget");
let value = inputBox.value;
```
- `getElementById()` selects the input field.
- `.value` gets the text entered by the user.

---

### 4. Prevent Empty Input
```javascript
if (value == "") return;
```
If the input is empty, the function stops.

---

### 5. Store Task in Array
```javascript
list.push(value);
```
Adds the task into the array.

---

### 6. Create List Item
```javascript
let li = document.createElement("li");
```
Creates a new list item element.

---

### 7. Create Text Span
```javascript
let span = document.createElement("span");
span.innerText = value;
```
- A `span` is created to hold the task text.
- `innerText` sets the text.

---

### 8. Add Span to List Item
```javascript
li.appendChild(span);
```

---

### 9. Mark Task as Completed
```javascript
li.onclick = function () {
    li.classList.toggle("done");
};
```
- When the list item is clicked, it toggles the class "done".
- `classList.toggle()` adds/removes the class.

---

### 10. Delete Button
```javascript
let delBtn = document.createElement("button");
delBtn.innerText = "delete";
```

#### Delete Logic
```javascript
delBtn.onclick = function (event) {
    event.stopPropagation();

    li.remove();

    list = list.filter(function (item) {
        return item !== span.innerText;
    });
};
```

Explanation:
- `event.stopPropagation()` prevents the parent click event.
- `li.remove()` deletes the task from UI.
- `filter()` removes the task from the array.

---

### 11. Edit Button
```javascript
let editBtn = document.createElement("button");
editBtn.innerText = "edit";
```

#### Edit Logic
```javascript
editBtn.onclick = function (event) {
    event.stopPropagation();

    let inputEdit = document.createElement("input");
    inputEdit.value = span.innerText;

    li.replaceChild(inputEdit, span);

    editBtn.innerText = "save";
```

Explanation:
- Creates an input box for editing.
- Replaces the text with input field.
- Changes button text to "save".

---

### 12. Save Edited Task
```javascript
editBtn.onclick = function (event) {
    event.stopPropagation();

    span.innerText = inputEdit.value;

    list = list.map(function (item) {
        if (item === value) {
            return inputEdit.value;
        } else {
            return item;
        }
    });

    li.replaceChild(span, inputEdit);

    editBtn.innerText = "edit";
};
```

Explanation:
- Updates the text with new value.
- `map()` updates the array.
- Restores the span.
- Changes button back to "edit".

---

### 13. Append Buttons
```javascript
li.appendChild(editBtn);
li.appendChild(delBtn);
```

---

### 14. Add Task to UI
```javascript
document.getElementById("result").appendChild(li);
```

---

### 15. Clear Input Field
```javascript
inputBox.value = "";
```

---

## How to Run
1. Download or clone the project
2. Open index.html in browser

---

## Future Improvements
- Store tasks in localStorage
- Improve UI design
- Add responsiveness

---

## Author
Vinayagam

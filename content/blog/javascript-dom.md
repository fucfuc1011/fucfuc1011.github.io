---
title: "DOM Manipulation - Thao tác với HTML"
date: 2025-09-28
category: "JavaScript"
image: "/images/posts/javascript-dom.jpg"
---

## DOM là gì?

DOM (Document Object Model) là giao diện lập trình cho HTML. Nó biểu diễn cấu trúc trang web dưới dạng cây (tree) các object, cho phép JavaScript thay đổi nội dung, cấu trúc và style của trang web.

## Truy cập phần tử HTML

### 1. getElementById

```javascript
// HTML: <div id="myDiv">Nội dung</div>
let element = document.getElementById("myDiv");
console.log(element.textContent); // Nội dung
```

### 2. getElementsByClassName

```javascript
// HTML: <p class="text">Đoạn 1</p> <p class="text">Đoạn 2</p>
let elements = document.getElementsByClassName("text");
console.log(elements.length); // 2
console.log(elements[0].textContent); // Đoạn 1
```

### 3. getElementsByTagName

```javascript
// Lấy tất cả thẻ p
let paragraphs = document.getElementsByTagName("p");
for (let p of paragraphs) {
    console.log(item.textContent);
});
```

## Thay đổi nội dung

### innerHTML vs textContent

```javascript
let div = document.querySelector("#myDiv");

// textContent: Chỉ text thuần
div.textContent = "Xin chào";

// innerHTML: Có thể chứa HTML
div.innerHTML = "<strong>Xin chào</strong>";

// innerText: Giống textContent nhưng chỉ lấy text hiển thị
div.innerText = "Hello";
```

### Ví dụ thực tế

```html
<!DOCTYPE html>
<html>
<body>
    <h1 id="title">Tiêu đề cũ</h1>
    <button onclick="changeTitle()">Đổi tiêu đề</button>
    
    <script>
        function changeTitle() {
            let title = document.getElementById("title");
            title.innerHTML = "Tiêu đề <strong>mới</strong>!";
        }
    </script>
</body>
</html>
```

## Thay đổi thuộc tính (Attributes)

```javascript
let img = document.querySelector("img");

// Lấy thuộc tính
let src = img.getAttribute("src");

// Đặt thuộc tính
img.setAttribute("src", "new-image.jpg");
img.setAttribute("alt", "Mô tả ảnh");

// Cách ngắn gọn
img.src = "new-image.jpg";
img.alt = "Mô tả ảnh";

// Xóa thuộc tính
img.removeAttribute("title");
```

## Thay đổi Style CSS

```javascript
let div = document.querySelector("#myDiv");

// Thay đổi từng thuộc tính
div.style.color = "red";
div.style.fontSize = "20px";
div.style.backgroundColor = "yellow";
div.style.padding = "10px";
div.style.border = "2px solid black";

// Nhiều style cùng lúc
div.style.cssText = `
    color: blue;
    font-size: 24px;
    background-color: lightgray;
    padding: 15px;
`;
```

## Thao tác với Class

```javascript
let element = document.querySelector("#myElement");

// Thêm class
element.classList.add("active");

// Xóa class
element.classList.remove("old-class");

// Toggle class (có thì xóa, không có thì thêm)
element.classList.toggle("highlight");

// Kiểm tra có class không
if (element.classList.contains("active")) {
    console.log("Element đang active");
}

// Thay thế class
element.classList.replace("old", "new");
```

## Tạo và xóa phần tử

### Tạo phần tử mới

```javascript
// Tạo phần tử
let newDiv = document.createElement("div");
newDiv.textContent = "Đây là div mới";
newDiv.className = "my-class";
newDiv.id = "newDiv";

// Thêm vào cuối body
document.body.appendChild(newDiv);

// Thêm vào một phần tử khác
let container = document.querySelector("#container");
container.appendChild(newDiv);

// Thêm vào đầu
container.insertBefore(newDiv, container.firstChild);
```

### Xóa phần tử

```javascript
let element = document.querySelector("#myElement");

// Cách 1: remove()
element.remove();

// Cách 2: removeChild()
let parent = element.parentElement;
parent.removeChild(element);
```

## Event Handling (Xử lý sự kiện)

### addEventListener

```javascript
let button = document.querySelector("#myButton");

// Click event
button.addEventListener("click", function() {
    alert("Button đã được click!");
});

// Arrow function
button.addEventListener("click", () => {
    console.log("Clicked!");
});

// Function riêng
function handleClick() {
    console.log("Button clicked");
}
button.addEventListener("click", handleClick);
```

### Các event phổ biến

```javascript
let input = document.querySelector("#myInput");

// Input events
input.addEventListener("focus", () => {
    console.log("Input được focus");
});

input.addEventListener("blur", () => {
    console.log("Input mất focus");
});

input.addEventListener("input", (e) => {
    console.log("Giá trị: " + e.target.value);
});

input.addEventListener("change", () => {
    console.log("Giá trị đã thay đổi");
});

// Keyboard events
document.addEventListener("keydown", (e) => {
    console.log("Phím được nhấn: " + e.key);
});

// Mouse events
let box = document.querySelector("#box");

box.addEventListener("mouseenter", () => {
    box.style.backgroundColor = "lightblue";
});

box.addEventListener("mouseleave", () => {
    box.style.backgroundColor = "lightgray";
});
```

## Event Object

```javascript
let button = document.querySelector("#myButton");

button.addEventListener("click", function(event) {
    // event object chứa thông tin về sự kiện
    console.log("Type:", event.type);           // click
    console.log("Target:", event.target);       // element được click
    console.log("Position:", event.clientX, event.clientY);
    
    // Ngăn hành động mặc định
    event.preventDefault();
    
    // Ngăn event lan truyền
    event.stopPropagation();
});
```

## Ví dụ thực hành

### Ví dụ 1: Todo List

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .completed { 
            text-decoration: line-through; 
            color: gray; 
        }
    </style>
</head>
<body>
    <h1>Todo List</h1>
    <input type="text" id="taskInput" placeholder="Nhập công việc...">
    <button id="addBtn">Thêm</button>
    <ul id="taskList"></ul>
    
    <script>
        const input = document.getElementById("taskInput");
        const addBtn = document.getElementById("addBtn");
        const taskList = document.getElementById("taskList");
        
        addBtn.addEventListener("click", addTask);
        input.addEventListener("keypress", (e) => {
            if (e.key === "Enter") addTask();
        });
        
        function addTask() {
            const task = input.value.trim();
            if (task === "") return;
            
            // Tạo li
            const li = document.createElement("li");
            li.textContent = task;
            
            // Click để hoàn thành
            li.addEventListener("click", function() {
                this.classList.toggle("completed");
            });
            
            // Nút xóa
            const deleteBtn = document.createElement("button");
            deleteBtn.textContent = "Xóa";
            deleteBtn.style.marginLeft = "10px";
            deleteBtn.addEventListener("click", function(e) {
                e.stopPropagation();
                li.remove();
            });
            
            li.appendChild(deleteBtn);
            taskList.appendChild(li);
            input.value = "";
            input.focus();
        }
    </script>
</body>
</html>
```

### Ví dụ 2: Form Validation

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .error { color: red; font-size: 14px; }
        .input-error { border: 2px solid red; }
    </style>
</head>
<body>
    <form id="myForm">
        <div>
            <label>Tên:</label>
            <input type="text" id="name" required>
            <span class="error" id="nameError"></span>
        </div>
        
        <div>
            <label>Email:</label>
            <input type="email" id="email" required>
            <span class="error" id="emailError"></span>
        </div>
        
        <div>
            <label>Số điện thoại:</label>
            <input type="text" id="phone" required>
            <span class="error" id="phoneError"></span>
        </div>
        
        <button type="submit">Đăng ký</button>
    </form>
    
    <script>
        const form = document.getElementById("myForm");
        const nameInput = document.getElementById("name");
        const emailInput = document.getElementById("email");
        const phoneInput = document.getElementById("phone");
        
        form.addEventListener("submit", function(e) {
            e.preventDefault();
            
            let isValid = true;
            
            // Clear errors
            clearErrors();
            
            // Validate name
            if (nameInput.value.trim() === "") {
                showError("name", "Tên không được để trống");
                isValid = false;
            } else if (nameInput.value.trim().length < 2) {
                showError("name", "Tên phải có ít nhất 2 ký tự");
                isValid = false;
            }
            
            // Validate email
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailRegex.test(emailInput.value)) {
                showError("email", "Email không hợp lệ");
                isValid = false;
            }
            
            // Validate phone
            const phoneRegex = /^0[0-9]{9}$/;
            if (!phoneRegex.test(phoneInput.value)) {
                showError("phone", "Số điện thoại không hợp lệ (10 số, bắt đầu bằng 0)");
                isValid = false;
            }
            
            if (isValid) {
                alert("Đăng ký thành công!");
                form.reset();
            }
        });
        
        function showError(fieldId, message) {
            const errorSpan = document.getElementById(fieldId + "Error");
            const input = document.getElementById(fieldId);
            
            errorSpan.textContent = message;
            input.classList.add("input-error");
        }
        
        function clearErrors() {
            const errors = document.querySelectorAll(".error");
            errors.forEach(error => error.textContent = "");
            
            const inputs = document.querySelectorAll("input");
            inputs.forEach(input => input.classList.remove("input-error"));
        }
    </script>
</body>
</html>
```

### Ví dụ 3: Counter đơn giản

```html
<!DOCTYPE html>
<html>
<body>
    <h1>Counter App</h1>
    <h2 id="count">0</h2>
    <button id="decrease">-</button>
    <button id="reset">Reset</button>
    <button id="increase">+</button>
    
    <script>
        let count = 0;
        const countDisplay = document.getElementById("count");
        const decreaseBtn = document.getElementById("decrease");
        const resetBtn = document.getElementById("reset");
        const increaseBtn = document.getElementById("increase");
        
        function updateDisplay() {
            countDisplay.textContent = count;
            
            // Đổi màu theo giá trị
            if (count > 0) {
                countDisplay.style.color = "green";
            } else if (count < 0) {
                countDisplay.style.color = "red";
            } else {
                countDisplay.style.color = "black";
            }
        }
        
        increaseBtn.addEventListener("click", () => {
            count++;
            updateDisplay();
        });
        
        decreaseBtn.addEventListener("click", () => {
            count--;
            updateDisplay();
        });
        
        resetBtn.addEventListener("click", () => {
            count = 0;
            updateDisplay();
        });
    </script>
</body>
</html>
```

## Best Practices

1. **Sử dụng querySelector/querySelectorAll** thay vì getElementById
2. **Cache DOM references** để tránh truy vấn nhiều lần
3. **Event Delegation** cho các element động
4. **Tránh innerHTML** khi có thể (bảo mật)
5. **Sử dụng classList** thay vì className

```javascript
// ✓ Tốt: Cache element
const button = document.querySelector("#myButton");
button.addEventListener("click", handleClick);
button.textContent = "Click me";

// ✗ Không tốt: Truy vấn nhiều lần
document.querySelector("#myButton").addEventListener("click", handleClick);
document.querySelector("#myButton").textContent = "Click me";
```

## Kết luận

DOM Manipulation là kỹ năng quan trọng để tạo ra các trang web tương tác. Việc thành thạo cách truy cập, thay đổi và xử lý sự kiện của các phần tử HTML sẽ giúp bạn xây dựng được những ứng dụng web mạnh mẽ và thân thiện với người dùng. Hãy thực hành nhiều với các ví dụ trên để nắm vững kiến thức này!

---

**Chúc bạn học tập thành công!** 🎉(p.textContent);
}
```

### 4. querySelector (Khuyên dùng)

```javascript
// Lấy phần tử đầu tiên
let first = document.querySelector(".text");
let firstP = document.querySelector("p");
let byId = document.querySelector("#myDiv");
```

### 5. querySelectorAll (Khuyên dùng)

```javascript
// Lấy tất cả phần tử
let all = document.querySelectorAll(".text");
all.forEach(item => {
    console.log
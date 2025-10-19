---
title: "JavaScript là gì? Bắt đầu với JavaScript"
date: 2024-09-25
category: "JavaScript"
image: "/images/posts/javascript-gioi-thieu.jpg"
---

## JavaScript là gì?

JavaScript là ngôn ngữ lập trình phổ biến nhất thế giới, được sử dụng để tạo ra các trang web tương tác và ứng dụng web động. Ban đầu, JavaScript chỉ chạy trên trình duyệt, nhưng hiện nay với Node.js, JavaScript có thể chạy cả trên server.

## Tại sao nên học JavaScript?

### 1. Dễ học
JavaScript có cú pháp đơn giản, thân thiện với người mới bắt đầu.

### 2. Phổ biến
- Mọi trang web hiện đại đều sử dụng JavaScript
- Có cộng đồng lớn và nhiều tài liệu học tập

### 3. Đa năng
- **Frontend**: React, Vue, Angular
- **Backend**: Node.js, Express
- **Mobile**: React Native, Ionic
- **Desktop**: Electron

### 4. Cơ hội việc làm
JavaScript developers luôn được săn đón với mức lương cao.

## JavaScript chạy ở đâu?

### 1. Trên trình duyệt
JavaScript chạy trực tiếp trên trình duyệt (Chrome, Firefox, Safari, Edge).

```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Example</title>
</head>
<body>
    <h1>Hello JavaScript!</h1>
    
    <script>
        console.log("JavaScript đang chạy!");
        alert("Chào mừng bạn đến với JavaScript!");
    </script>
</body>
</html>
```

### 2. Trên Node.js
JavaScript có thể chạy trên máy tính với Node.js.

```javascript
// Lưu file: hello.js
console.log("Hello from Node.js!");

// Chạy: node hello.js
```

## Cách thêm JavaScript vào HTML

### 1. Inline JavaScript

```html
<button onclick="alert('Bạn đã click!')">Click me</button>
```

### 2. Internal JavaScript

```html
<!DOCTYPE html>
<html>
<body>
    <h1 id="title">Tiêu đề</h1>
    
    <script>
        document.getElementById("title").innerHTML = "JavaScript đang hoạt động!";
    </script>
</body>
</html>
```

### 3. External JavaScript (Khuyên dùng)

```html
<!DOCTYPE html>
<html>
<body>
    <h1>My Website</h1>
    
    <!-- Link file JavaScript -->
    <script src="script.js"></script>
</body>
</html>
```

File `script.js`:
```javascript
console.log("JavaScript từ file external!");
```

## Chương trình JavaScript đầu tiên

```javascript
// In ra console
console.log("Hello, World!");

// Hiển thị hộp thoại
alert("Đây là alert box!");

// Nhập dữ liệu từ người dùng
let name = prompt("Tên bạn là gì?");
console.log("Xin chào " + name);

// Thay đổi nội dung HTML
document.write("<h2>JavaScript thật tuyệt vời!</h2>");
```

## Console - Công cụ quan trọng

Console là công cụ để debug và kiểm tra code JavaScript.

### Mở Console:
- **Chrome/Edge**: F12 hoặc Ctrl + Shift + J
- **Firefox**: F12 hoặc Ctrl + Shift + K
- **Safari**: Cmd + Option + C

### Các lệnh Console phổ biến:

```javascript
// In ra console
console.log("Thông tin");

// In cảnh báo
console.warn("Cảnh báo!");

// In lỗi
console.error("Đã có lỗi xảy ra!");

// In bảng
console.table([{name: "An", age: 20}, {name: "Bình", age: 22}]);

// Xóa console
console.clear();
```

## Comment trong JavaScript

```javascript
// Đây là comment một dòng

/*
   Đây là comment
   nhiều dòng
*/

/**
 * Đây là JSDoc comment
 * Dùng để mô tả function
 */
```

## Ví dụ thực hành

### Ví dụ 1: Thay đổi nội dung và màu sắc

```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Demo</title>
</head>
<body>
    <h1 id="myHeading">Tiêu đề gốc</h1>
    <button onclick="changeContent()">Thay đổi</button>
    
    <script>
        function changeContent() {
            let heading = document.getElementById("myHeading");
            heading.innerHTML = "Tiêu đề mới!";
            heading.style.color = "blue";
        }
    </script>
</body>
</html>
```

### Ví dụ 2: Tính toán đơn giản

```html
<!DOCTYPE html>
<html>
<body>
    <h2>Máy tính đơn giản</h2>
    
    <input type="number" id="num1" placeholder="Số thứ nhất">
    <input type="number" id="num2" placeholder="Số thứ hai">
    <button onclick="calculate()">Tính tổng</button>
    
    <p id="result"></p>
    
    <script>
        function calculate() {
            let a = parseFloat(document.getElementById("num1").value);
            let b = parseFloat(document.getElementById("num2").value);
            let sum = a + b;
            
            document.getElementById("result").innerHTML = "Kết quả: " + sum;
        }
    </script>
</body>
</html>
```

## Công cụ cần thiết

### 1. Code Editor:
- **Visual Studio Code** (khuyên dùng)
- Sublime Text
- Atom

### 2. Trình duyệt:
- Google Chrome (khuyên dùng)
- Firefox Developer Edition

### 3. Extension hữu ích cho VS Code:
- Live Server - Chạy web local
- JavaScript (ES6) code snippets
- Prettier - Code formatter

## Roadmap học JavaScript

1. **Cơ bản**: Biến, kiểu dữ liệu, toán tử
2. **Câu lệnh điều khiển**: if-else, switch, vòng lặp
3. **Functions**: Khai báo, arrow functions
4. **DOM Manipulation**: Thao tác với HTML
5. **Events**: Xử lý sự kiện
6. **ES6+**: Template literals, destructuring, spread operator
7. **Asynchronous**: Promises, Async/Await
8. **API**: Fetch, Axios

## Kết luận

JavaScript là ngôn ngữ không thể thiếu trong phát triển web hiện đại. Với JavaScript, bạn có thể tạo ra những trang web tương tác, ứng dụng web mạnh mẽ, thậm chí cả mobile app và desktop app. Trong bài viết tiếp theo, chúng ta sẽ tìm hiểu về biến, kiểu dữ liệu và toán tử trong JavaScript!
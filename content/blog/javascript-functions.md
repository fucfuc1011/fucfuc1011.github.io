---
title: "Functions và Arrow Functions trong ES6"
date: 2025-09-27
category: "JavaScript"
image: "/images/posts/javascript-functions.jpg"
---

## Function là gì?

Function (hàm) là một khối code có thể tái sử dụng, thực hiện một nhiệm vụ cụ thể. Function giúp code gọn gàng, dễ bảo trì và tránh lặp code.

## Cách khai báo Function

### 1. Function Declaration

```javascript
// Khai báo function
function chaoHoi() {
    console.log("Xin chào!");
}

// Gọi function
chaoHoi(); // Xin chào!

// Function với tham số
function chaoTen(ten) {
    console.log("Xin chào " + ten);
}

chaoTen("Phúc");  // Xin chào Phúc
chaoTen("An");    // Xin chào An
```

### 2. Function Expression

```javascript
// Gán function vào biến
const tinhTong = function(a, b) {
    return a + b;
};

let ketQua = tinhTong(5, 3);
console.log(ketQua); // 8
```

### 3. Arrow Function (ES6) - Khuyên dùng

```javascript
// Cú pháp đầy đủ
const tinhTich = (a, b) => {
    return a * b;
};

// Cú pháp ngắn gọn (một biểu thức)
const tinhHieu = (a, b) => a - b;

// Một tham số (bỏ được dấu ngoặc)
const binhPhuong = x => x * x;

// Không có tham số
const sayHello = () => console.log("Hello!");

// Ví dụ
console.log(tinhTich(4, 5));  // 20
console.log(tinhHieu(10, 3)); // 7
console.log(binhPhuong(5));   // 25
sayHello();                   // Hello!
```

## Return trong Function

```javascript
// Function có return
function tinhDienTich(dai, rong) {
    return dai * rong;
}

let dienTich = tinhDienTich(5, 3);
console.log(dienTich); // 15

// Function không có return (return undefined)
function inThongTin(ten) {
    console.log("Tên: " + ten);
}

let result = inThongTin("Phúc");
console.log(result); // undefined
```

## Tham số mặc định (Default Parameters)

```javascript
// ES6: Tham số mặc định
function chaoHoi(ten = "Khách") {
    console.log(`Xin chào ${ten}!`);
}

chaoHoi("Phúc"); // Xin chào Phúc!
chaoHoi();       // Xin chào Khách!

// Với số
const tinhLaiSuat = (tien, laiSuat = 5) => {
    return tien * laiSuat / 100;
};

console.log(tinhLaiSuat(1000000));     // 50000
console.log(tinhLaiSuat(1000000, 10)); // 100000
```

## Rest Parameters

```javascript
// Nhận nhiều tham số
function tinhTong(...numbers) {
    let sum = 0;
    for (let num of numbers) {
        sum += num;
    }
    return sum;
}

console.log(tinhTong(1, 2, 3));       // 6
console.log(tinhTong(1, 2, 3, 4, 5)); // 15

// Arrow function với rest parameters
const timMax = (...nums) => Math.max(...nums);

console.log(timMax(10, 5, 20, 15)); // 20
```

## Scope (Phạm vi)

### Global Scope

```javascript
let globalVar = "Tôi là biến global";

function showGlobal() {
    console.log(globalVar); // Truy cập được
}

showGlobal(); // Tôi là biến global
console.log(globalVar); // Tôi là biến global
```

### Local Scope

```javascript
function myFunction() {
    let localVar = "Tôi là biến local";
    console.log(localVar); // OK
}

myFunction();
// console.log(localVar); // Lỗi! Không truy cập được
```

### Block Scope (let, const)

```javascript
if (true) {
    let x = 10;
    const y = 20;
    var z = 30;
}

// console.log(x); // Lỗi!
// console.log(y); // Lỗi!
console.log(z);    // 30 (var không có block scope)
```

## Callback Function

Function được truyền như tham số cho function khác.

```javascript
function processArray(arr, callback) {
    let result = [];
    for (let item of arr) {
        result.push(callback(item));
    }
    return result;
}

// Callback: nhân đôi
let numbers = [1, 2, 3, 4, 5];
let doubled = processArray(numbers, x => x * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// Callback: bình phương
let squared = processArray(numbers, x => x ** 2);
console.log(squared); // [1, 4, 9, 16, 25]
```

## Higher-Order Functions

Function nhận function khác làm tham số hoặc trả về function.

```javascript
// map: Biến đổi mỗi phần tử
let numbers = [1, 2, 3, 4, 5];
let doubled = numbers.map(x => x * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// filter: Lọc phần tử
let evenNumbers = numbers.filter(x => x % 2 === 0);
console.log(evenNumbers); // [2, 4]

// reduce: Tính tổng
let sum = numbers.reduce((total, current) => total + current, 0);
console.log(sum); // 15

// forEach: Duyệt mảng
numbers.forEach(x => console.log(x));
```

## Closure

Function bên trong có thể truy cập biến của function bên ngoài.

```javascript
function taoCounter() {
    let count = 0;
    
    return function() {
        count++;
        return count;
    };
}

let counter1 = taoCounter();
console.log(counter1()); // 1
console.log(counter1()); // 2
console.log(counter1()); // 3

let counter2 = taoCounter();
console.log(counter2()); // 1 (counter mới)
```

## IIFE (Immediately Invoked Function Expression)

Function tự gọi ngay khi khai báo.

```javascript
(function() {
    console.log("Function này chạy ngay!");
})();

// IIFE với arrow function
(() => {
    console.log("Arrow IIFE!");
})();

// IIFE với tham số
((name) => {
    console.log(`Hello ${name}!`);
})("Phúc");
```

## Ví dụ thực hành

### Ví dụ 1: Máy tính đơn giản

```javascript
const calculator = {
    add: (a, b) => a + b,
    subtract: (a, b) => a - b,
    multiply: (a, b) => a * b,
    divide: (a, b) => b !== 0 ? a / b : "Không thể chia cho 0"
};

console.log(calculator.add(10, 5));      // 15
console.log(calculator.subtract(10, 5)); // 5
console.log(calculator.multiply(10, 5)); // 50
console.log(calculator.divide(10, 5));   // 2
console.log(calculator.divide(10, 0));   // Không thể chia cho 0
```

### Ví dụ 2: Xử lý mảng sinh viên

```javascript
const students = [
    {name: "An", score: 8.5},
    {name: "Bình", score: 6.0},
    {name: "Cường", score: 9.0},
    {name: "Dũng", score: 7.5}
];

// Tìm sinh viên điểm cao nhất
const findTopStudent = (students) => {
    return students.reduce((top, current) => 
        current.score > top.score ? current : top
    );
};

// Lọc sinh viên giỏi (>= 8.0)
const getGoodStudents = (students) => {
    return students.filter(s => s.score >= 8.0);
};

// Tính điểm trung bình
const getAverageScore = (students) => {
    let total = students.reduce((sum, s) => sum + s.score, 0);
    return total / students.length;
};

console.log("Sinh viên xuất sắc:", findTopStudent(students));
console.log("Sinh viên giỏi:", getGoodStudents(students));
console.log("Điểm TB:", getAverageScore(students).toFixed(2));
```

### Ví dụ 3: Tạo validator

```javascript
const validator = {
    isEmail: (email) => {
        const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return regex.test(email);
    },
    
    isPhoneNumber: (phone) => {
        const regex = /^(0|\+84)[0-9]{9}$/;
        return regex.test(phone);
    },
    
    isStrongPassword: (password) => {
        return password.length >= 8 && 
               /[A-Z]/.test(password) && 
               /[a-z]/.test(password) && 
               /[0-9]/.test(password);
    }
};

console.log(validator.isEmail("test@email.com"));     // true
console.log(validator.isEmail("invalid-email"));      // false
console.log(validator.isPhoneNumber("0912345678"));   // true
console.log(validator.isStrongPassword("Pass123"));   // true
console.log(validator.isStrongPassword("weak"));      // false
```

## So sánh Function Declaration vs Arrow Function

| Đặc điểm | Function Declaration | Arrow Function |
|----------|---------------------|----------------|
| Cú pháp | Dài hơn | Ngắn gọn |
| `this` | Có context riêng | Kế thừa từ parent |
| Hoisting | Có | Không |
| Constructor | Có thể dùng | Không thể |
| arguments | Có | Không (dùng rest) |

## Kết luận

Functions là trái tim của JavaScript. Arrow functions trong ES6 giúp code ngắn gọn và dễ đọc hơn. Hiểu rõ về functions, callbacks, và higher-order functions sẽ giúp bạn viết code JavaScript hiệu quả và chuyên nghiệp hơn. Trong bài viết tiếp theo, chúng ta sẽ tìm hiểu về DOM Manipulation - cách thao tác với HTML!
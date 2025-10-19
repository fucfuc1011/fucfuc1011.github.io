---
title: "Biến, kiểu dữ liệu và toán tử trong JavaScript"
date: 2025-09-26
category: "JavaScript"
image: "/images/posts/javascript-bien-kieu-du-lieu.jpg"
---

## Biến trong JavaScript

Biến là nơi lưu trữ dữ liệu. JavaScript có 3 cách khai báo biến:

### 1. var (Cách cũ - không khuyên dùng)

```javascript
var name = "Phúc";
var age = 25;
```

### 2. let (Khuyên dùng cho biến thay đổi)

```javascript
let city = "Hà Nội";
city = "TP.HCM"; // Có thể thay đổi giá trị
```

### 3. const (Khuyên dùng cho hằng số)

```javascript
const PI = 3.14159;
// PI = 3.14; // Lỗi! Không thể thay đổi const
```

### Quy tắc đặt tên biến:

```javascript
// ✓ Đúng
let firstName = "An";
let age2 = 20;
let _private = "data";
let $jquery = "selector";

// ✗ Sai
let 2age = 20;        // Không bắt đầu bằng số
let first-name = "An"; // Không dùng dấu gạch ngang
let class = "A";      // Không dùng từ khóa
```

## Kiểu dữ liệu trong JavaScript

JavaScript có 7 kiểu dữ liệu nguyên thủy (primitive):

### 1. String (Chuỗi)

```javascript
let name = "Nguyễn Văn An";
let greeting = 'Xin chào';
let message = `Hello ${name}`; // Template literal

// Các phương thức String
let text = "JavaScript";
console.log(text.length);           // 10
console.log(text.toUpperCase());    // JAVASCRIPT
console.log(text.toLowerCase());    // javascript
console.log(text.charAt(0));        // J
console.log(text.includes("Script")); // true
console.log(text.slice(0, 4));      // Java
```

### 2. Number (Số)

```javascript
let age = 25;              // Số nguyên
let price = 99.99;         // Số thực
let negative = -10;        // Số âm
let infinity = Infinity;   // Vô cực
let notNumber = NaN;       // Not a Number

// Phép toán
let sum = 10 + 5;     // 15
let diff = 10 - 5;    // 5
let product = 10 * 5; // 50
let quotient = 10 / 5; // 2
let remainder = 10 % 3; // 1
let power = 2 ** 3;    // 8
```

### 3. Boolean (Luận lý)

```javascript
let isStudent = true;
let isMarried = false;

// So sánh trả về boolean
let result1 = 5 > 3;   // true
let result2 = 10 < 5;  // false
let result3 = 5 === 5; // true
```

### 4. Undefined

```javascript
let x;
console.log(x); // undefined

let person = {name: "An"};
console.log(person.age); // undefined
```

### 5. Null

```javascript
let data = null; // Giá trị rỗng có chủ ý
```

### 6. Symbol (ES6)

```javascript
let id = Symbol("id");
```

### 7. BigInt (ES2020)

```javascript
let bigNumber = 1234567890123456789012345678901234567890n;
```

## Kiểu dữ liệu phức tạp

### Object (Đối tượng)

```javascript
let person = {
    name: "Phạm Thành Phúc",
    age: 25,
    city: "Hà Nội",
    isStudent: false
};

// Truy cập thuộc tính
console.log(person.name);        // Phạm Thành Phúc
console.log(person["age"]);      // 25

// Thêm thuộc tính
person.email = "phuc@email.com";

// Xóa thuộc tính
delete person.city;
```

### Array (Mảng)

```javascript
let fruits = ["Apple", "Banana", "Orange"];
let numbers = [1, 2, 3, 4, 5];
let mixed = [1, "Hello", true, null];

// Truy cập phần tử
console.log(fruits[0]); // Apple

// Độ dài mảng
console.log(fruits.length); // 3

// Thêm phần tử
fruits.push("Mango");      // Thêm cuối
fruits.unshift("Grape");   // Thêm đầu

// Xóa phần tử
fruits.pop();              // Xóa cuối
fruits.shift();            // Xóa đầu

// Duyệt mảng
for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}

// forEach
fruits.forEach(function(fruit) {
    console.log(fruit);
});
```

## Kiểm tra kiểu dữ liệu

```javascript
console.log(typeof "Hello");      // string
console.log(typeof 42);           // number
console.log(typeof true);         // boolean
console.log(typeof undefined);    // undefined
console.log(typeof null);         // object (bug của JS)
console.log(typeof [1, 2, 3]);    // object
console.log(typeof {name: "An"}); // object

// Kiểm tra Array
console.log(Array.isArray([1, 2, 3])); // true
```

## Chuyển đổi kiểu dữ liệu

### String sang Number

```javascript
let str = "123";

// Cách 1: Number()
let num1 = Number(str);  // 123

// Cách 2: parseInt()
let num2 = parseInt("123.45");  // 123

// Cách 3: parseFloat()
let num3 = parseFloat("123.45"); // 123.45

// Cách 4: Dùng +
let num4 = +"456"; // 456
```

### Number sang String

```javascript
let num = 123;

// Cách 1: String()
let str1 = String(num);  // "123"

// Cách 2: toString()
let str2 = num.toString(); // "123"

// Cách 3: Nối với chuỗi rỗng
let str3 = num + ""; // "123"
```

### Sang Boolean

```javascript
// Giá trị false: 0, "", null, undefined, NaN
console.log(Boolean(0));         // false
console.log(Boolean(""));        // false
console.log(Boolean(null));      // false
console.log(Boolean(undefined)); // false
console.log(Boolean(NaN));       // false

// Các giá trị khác là true
console.log(Boolean(1));         // true
console.log(Boolean("Hello"));   // true
console.log(Boolean([]));        // true
console.log(Boolean({}));        // true
```

## Toán tử trong JavaScript

### Toán tử số học

```javascript
let a = 10;
let b = 3;

console.log(a + b);  // 13 - Cộng
console.log(a - b);  // 7  - Trừ
console.log(a * b);  // 30 - Nhân
console.log(a / b);  // 3.333... - Chia
console.log(a % b);  // 1  - Chia lấy dư
console.log(a ** b); // 1000 - Lũy thừa

// Tăng giảm
let x = 5;
x++;  // x = 6 (tăng sau)
++x;  // x = 7 (tăng trước)
x--;  // x = 6 (giảm sau)
--x;  // x = 5 (giảm trước)
```

### Toán tử gán

```javascript
let x = 10;

x += 5;  // x = x + 5  → 15
x -= 3;  // x = x - 3  → 12
x *= 2;  // x = x * 2  → 24
x /= 4;  // x = x / 4  → 6
x %= 4;  // x = x % 4  → 2
```

### Toán tử so sánh

```javascript
// So sánh bằng
console.log(5 == "5");   // true (chỉ so sánh giá trị)
console.log(5 === "5");  // false (so sánh cả kiểu dữ liệu)

// So sánh khác
console.log(5 != "5");   // false
console.log(5 !== "5");  // true

// So sánh lớn nhỏ
console.log(10 > 5);     // true
console.log(10 < 5);     // false
console.log(10 >= 10);   // true
console.log(10 <= 5);    // false
```

### Toán tử logic

```javascript
let a = true;
let b = false;

// AND (&&) - Cả hai đều true
console.log(a && b);  // false
console.log(true && true); // true

// OR (||) - Một trong hai true
console.log(a || b);  // true
console.log(false || false); // false

// NOT (!) - Đảo ngược
console.log(!a);      // false
console.log(!b);      // true
```

### Toán tử 3 ngôi (Ternary)

```javascript
let age = 20;
let status = age >= 18 ? "Trưởng thành" : "Vị thành niên";
console.log(status); // Trưởng thành

// Tương đương với:
let status2;
if (age >= 18) {
    status2 = "Trưởng thành";
} else {
    status2 = "Vị thành niên";
}
```

## Template Literals (ES6)

```javascript
let name = "Phúc";
let age = 25;

// Cách cũ
let message1 = "Tên tôi là " + name + " và tôi " + age + " tuổi";

// Cách mới (Template Literal)
let message2 = `Tên tôi là ${name} và tôi ${age} tuổi`;

// Nhiều dòng
let html = `
    <div>
        <h1>${name}</h1>
        <p>Tuổi: ${age}</p>
    </div>
`;

// Tính toán trong template
let price = 100;
console.log(`Giá sau thuế: ${price * 1.1} VNĐ`);
```

## Ví dụ thực hành

### Ví dụ 1: Tính BMI

```javascript
let weight = 70; // kg
let height = 1.75; // m

let bmi = weight / (height ** 2);
let result;

if (bmi < 18.5) {
    result = "Thiếu cân";
} else if (bmi < 25) {
    result = "Bình thường";
} else if (bmi < 30) {
    result = "Thừa cân";
} else {
    result = "Béo phì";
}

console.log(`BMI: ${bmi.toFixed(2)} - ${result}`);
```

### Ví dụ 2: Quản lý danh sách sinh viên

```javascript
let students = [
    {name: "Nguyễn Văn An", score: 8.5},
    {name: "Trần Thị Bình", score: 9.0},
    {name: "Lê Văn Cường", score: 7.5}
];

console.log("=== DANH SÁCH SINH VIÊN ===");
students.forEach((student, index) => {
    let rank = student.score >= 8 ? "Giỏi" : 
               student.score >= 6.5 ? "Khá" : "Trung bình";
    console.log(`${index + 1}. ${student.name} - ${student.score} điểm - ${rank}`);
});

// Tính điểm trung bình
let totalScore = 0;
students.forEach(student => {
    totalScore += student.score;
});
let avgScore = totalScore / students.length;
console.log(`\nĐiểm trung bình lớp: ${avgScore.toFixed(2)}`);
```

## Kết luận

Biến, kiểu dữ liệu và toán tử là nền tảng của JavaScript. Hiểu rõ các khái niệm này sẽ giúp bạn viết code hiệu quả hơn. Trong bài viết tiếp theo, chúng ta sẽ tìm hiểu về Functions - một phần quan trọng trong JavaScript!
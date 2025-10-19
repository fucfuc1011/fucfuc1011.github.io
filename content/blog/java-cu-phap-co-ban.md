---
title: "Cú pháp cơ bản và kiểu dữ liệu trong Java"
date: 2021-10-02
category: "Java"
image: "/images/posts/java-cu-phap-co-ban.jpg"
---

## Biến trong Java

Biến là nơi lưu trữ dữ liệu trong chương trình. Trong Java, mỗi biến phải có kiểu dữ liệu xác định.

### Cú pháp khai báo biến:

```java
kieuDuLieu tenBien = giaTri;
```

**Ví dụ:**

```java
int age = 25;
String name = "Phạm Thành Phúc";
double salary = 15000.50;
boolean isStudent = true;
```

## Các kiểu dữ liệu trong Java

Java có hai loại kiểu dữ liệu chính:

### 1. Kiểu dữ liệu nguyên thủy (Primitive Types)

| Kiểu | Kích thước | Mô tả | Ví dụ |
|------|-----------|-------|-------|
| byte | 1 byte | Số nguyên từ -128 đến 127 | `byte x = 100;` |
| short | 2 bytes | Số nguyên từ -32,768 đến 32,767 | `short y = 5000;` |
| int | 4 bytes | Số nguyên từ -2³¹ đến 2³¹-1 | `int z = 100000;` |
| long | 8 bytes | Số nguyên rất lớn | `long a = 15000000000L;` |
| float | 4 bytes | Số thực độ chính xác đơn | `float b = 5.75f;` |
| double | 8 bytes | Số thực độ chính xác kép | `double c = 19.99d;` |
| boolean | 1 bit | Giá trị true/false | `boolean d = true;` |
| char | 2 bytes | Ký tự Unicode | `char e = 'A';` |

### 2. Kiểu dữ liệu tham chiếu (Reference Types)

```java
// String - Chuỗi ký tự
String message = "Hello Java";

// Array - Mảng
int[] numbers = {1, 2, 3, 4, 5};

// Object - Đối tượng
Person person = new Person("Phúc", 25);
```

## Toán tử trong Java

### Toán tử số học:

```java
int a = 10;
int b = 3;

int tong = a + b;        // 13 - Cộng
int hieu = a - b;        // 7  - Trừ
int tich = a * b;        // 30 - Nhân
int thuong = a / b;      // 3  - Chia
int du = a % b;          // 1  - Chia lấy dư
```

### Toán tử so sánh:

```java
int x = 5;
int y = 10;

boolean result1 = (x == y);  // false - Bằng
boolean result2 = (x != y);  // true  - Khác
boolean result3 = (x > y);   // false - Lớn hơn
boolean result4 = (x < y);   // true  - Nhỏ hơn
boolean result5 = (x >= y);  // false - Lớn hơn hoặc bằng
boolean result6 = (x <= y);  // true  - Nhỏ hơn hoặc bằng
```

### Toán tử logic:

```java
boolean a = true;
boolean b = false;

boolean and = a && b;  // false - AND (và)
boolean or = a || b;   // true  - OR (hoặc)
boolean not = !a;      // false - NOT (phủ định)
```

## Input và Output

### Output - Xuất dữ liệu:

```java
System.out.println("In ra và xuống dòng");
System.out.print("In ra không xuống dòng");
System.out.printf("Định dạng: %d, %s, %.2f", 10, "text", 3.14);
```

### Input - Nhập dữ liệu:

```java
import java.util.Scanner;

public class InputExample {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Nhập tên: ");
        String name = scanner.nextLine();
        
        System.out.print("Nhập tuổi: ");
        int age = scanner.nextInt();
        
        System.out.println("Xin chào " + name + ", " + age + " tuổi!");
        
        scanner.close();
    }
}
```

## Ví dụ thực hành

Viết chương trình tính diện tích hình chữ nhật:

```java
import java.util.Scanner;

public class TinhDienTich {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập chiều dài: ");
        double dai = sc.nextDouble();
        
        System.out.print("Nhập chiều rộng: ");
        double rong = sc.nextDouble();
        
        double dienTich = dai * rong;
        double chuVi = 2 * (dai + rong);
        
        System.out.println("Diện tích: " + dienTich);
        System.out.println("Chu vi: " + chuVi);
        
        sc.close();
    }
}
```

## Kết luận

Trong bài viết này, chúng ta đã tìm hiểu về các kiểu dữ liệu, biến, toán tử và cách nhập/xuất dữ liệu trong Java. Đây là những kiến thức nền tảng quan trọng để tiếp tục học các phần nâng cao hơn. Trong bài tiếp theo, chúng ta sẽ tìm hiểu về vòng lặp và câu lệnh điều kiện!
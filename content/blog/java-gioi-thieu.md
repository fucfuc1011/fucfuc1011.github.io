---
title: "Giới thiệu Java - Ngôn ngữ lập trình hướng đối tượng"
date: 2022-10-01
category: "Java"
image: "/images/posts/java-gioi-thieu.jpg"
---

## Java là gì?

Java là một ngôn ngữ lập trình hướng đối tượng (Object-Oriented Programming - OOP) được phát triển bởi Sun Microsystems vào năm 1995. Ngày nay, Java thuộc quyền sở hữu của Oracle Corporation và là một trong những ngôn ngữ lập trình phổ biến nhất thế giới.

## Đặc điểm nổi bật của Java

### 1. Độc lập nền tảng (Platform Independent)

Java có câu slogan nổi tiếng: **"Write Once, Run Anywhere"** (Viết một lần, chạy mọi nơi). Điều này có nghĩa là code Java có thể chạy trên bất kỳ hệ điều hành nào có cài đặt Java Virtual Machine (JVM).

```java
// Code Java này có thể chạy trên Windows, Mac, Linux
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### 2. Hướng đối tượng (Object-Oriented)

Java được thiết kế hoàn toàn theo mô hình hướng đối tượng, giúp code dễ bảo trì, mở rộng và tái sử dụng.

### 3. Bảo mật cao (Secure)

Java cung cấp nhiều tính năng bảo mật như:
- Không có con trỏ (pointers) trực tiếp
- Quản lý bộ nhớ tự động (Garbage Collection)
- Kiểm tra bytecode trước khi thực thi

### 4. Hiệu suất cao (High Performance)

Với công nghệ JIT (Just-In-Time) compiler, Java có thể đạt hiệu suất gần bằng các ngôn ngữ như C/C++.

## Ứng dụng của Java

Java được sử dụng rộng rãi trong nhiều lĩnh vực:

- **Ứng dụng di động**: Android apps
- **Ứng dụng web**: Spring Boot, JSP, Servlets
- **Ứng dụng desktop**: JavaFX, Swing
- **Big Data**: Hadoop, Apache Spark
- **Hệ thống phân tán**: Microservices

## Cài đặt Java

Để bắt đầu lập trình Java, bạn cần:

1. **JDK (Java Development Kit)**: Tải từ trang Oracle hoặc OpenJDK
2. **IDE (Integrated Development Environment)**: 
   - IntelliJ IDEA (khuyên dùng)
   - Eclipse
   - NetBeans

## Chương trình Java đầu tiên

```java
public class FirstProgram {
    public static void main(String[] args) {
        System.out.println("Chào mừng đến với Java!");
        System.out.println("Java thật tuyệt vời!");
    }
}
```

**Giải thích:**
- `public class FirstProgram`: Khai báo class
- `public static void main(String[] args)`: Phương thức main - điểm bắt đầu của chương trình
- `System.out.println()`: In ra màn hình console

## Kết luận

Java là một ngôn ngữ mạnh mẽ, phổ biến và có cộng đồng lớn. Nó là lựa chọn tuyệt vời cho người mới bắt đầu học lập trình cũng như các developer chuyên nghiệp. Trong bài viết tiếp theo, chúng ta sẽ tìm hiểu về cú pháp cơ bản và các kiểu dữ liệu trong Java.
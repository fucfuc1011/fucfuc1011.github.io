---
title: "Vòng lặp và câu lệnh điều kiện trong Java"
date: 2021-10-03
category: "Java"
image: "/images/posts/java-vong-lap.jpg"
---

## Câu lệnh điều kiện

Câu lệnh điều kiện giúp chương trình đưa ra quyết định dựa trên các điều kiện nhất định.

### 1. Câu lệnh if

```java
int diem = 85;

if (diem >= 80) {
    System.out.println("Giỏi");
}
```

### 2. Câu lệnh if-else

```java
int tuoi = 16;

if (tuoi >= 18) {
    System.out.println("Đã đủ tuổi bầu cử");
} else {
    System.out.println("Chưa đủ tuổi bầu cử");
}
```

### 3. Câu lệnh if-else if-else

```java
int diem = 75;

if (diem >= 90) {
    System.out.println("Xuất sắc");
} else if (diem >= 80) {
    System.out.println("Giỏi");
} else if (diem >= 70) {
    System.out.println("Khá");
} else if (diem >= 50) {
    System.out.println("Trung bình");
} else {
    System.out.println("Yếu");
}
```

### 4. Switch-case

```java
int thu = 3;

switch (thu) {
    case 2:
        System.out.println("Thứ Hai");
        break;
    case 3:
        System.out.println("Thứ Ba");
        break;
    case 4:
        System.out.println("Thứ Tư");
        break;
    default:
        System.out.println("Ngày khác");
}
```

## Vòng lặp

Vòng lặp giúp thực hiện một đoạn code nhiều lần.

### 1. Vòng lặp for

Dùng khi biết trước số lần lặp:

```java
// In số từ 1 đến 5
for (int i = 1; i <= 5; i++) {
    System.out.println("Số: " + i);
}
```

**Ví dụ: Tính tổng từ 1 đến 100**

```java
int tong = 0;
for (int i = 1; i <= 100; i++) {
    tong += i;
}
System.out.println("Tổng: " + tong); // 5050
```

### 2. Vòng lặp while

Dùng khi không biết trước số lần lặp, chỉ biết điều kiện:

```java
int count = 1;

while (count <= 5) {
    System.out.println("Count: " + count);
    count++;
}
```

**Ví dụ: Nhập số cho đến khi nhập 0**

```java
Scanner sc = new Scanner(System.in);
int number = -1;

while (number != 0) {
    System.out.print("Nhập số (0 để dừng): ");
    number = sc.nextInt();
    System.out.println("Bạn đã nhập: " + number);
}
```

### 3. Vòng lặp do-while

Giống while nhưng luôn thực hiện ít nhất 1 lần:

```java
int i = 1;

do {
    System.out.println("Giá trị: " + i);
    i++;
} while (i <= 5);
```

### 4. Vòng lặp for-each

Dùng để duyệt mảng hoặc collection:

```java
int[] numbers = {10, 20, 30, 40, 50};

for (int num : numbers) {
    System.out.println(num);
}

String[] names = {"An", "Bình", "Chi"};

for (String name : names) {
    System.out.println("Tên: " + name);
}
```

## Lệnh break và continue

### break - Thoát khỏi vòng lặp

```java
for (int i = 1; i <= 10; i++) {
    if (i == 6) {
        break; // Dừng vòng lặp khi i = 6
    }
    System.out.println(i);
}
// In ra: 1 2 3 4 5
```

### continue - Bỏ qua lần lặp hiện tại

```java
for (int i = 1; i <= 10; i++) {
    if (i % 2 == 0) {
        continue; // Bỏ qua số chẵn
    }
    System.out.println(i);
}
// In ra: 1 3 5 7 9
```

## Bài tập thực hành

### Bài 1: In bảng cửu chương

```java
public class BangCuuChuong {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập số cần in bảng cửu chương: ");
        int n = sc.nextInt();
        
        System.out.println("Bảng cửu chương " + n + ":");
        for (int i = 1; i <= 10; i++) {
            System.out.println(n + " x " + i + " = " + (n * i));
        }
    }
}
```

### Bài 2: Kiểm tra số nguyên tố

```java
public class SoNguyenTo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Nhập số cần kiểm tra: ");
        int n = sc.nextInt();
        
        boolean laSoNguyenTo = true;
        
        if (n < 2) {
            laSoNguyenTo = false;
        } else {
            for (int i = 2; i <= Math.sqrt(n); i++) {
                if (n % i == 0) {
                    laSoNguyenTo = false;
                    break;
                }
            }
        }
        
        if (laSoNguyenTo) {
            System.out.println(n + " là số nguyên tố");
        } else {
            System.out.println(n + " không là số nguyên tố");
        }
    }
}
```

### Bài 3: Tìm số lớn nhất trong mảng

```java
public class TimSoLonNhat {
    public static void main(String[] args) {
        int[] arr = {23, 45, 12, 67, 89, 34, 56};
        
        int max = arr[0];
        
        for (int num : arr) {
            if (num > max) {
                max = num;
            }
        }
        
        System.out.println("Số lớn nhất: " + max);
    }
}
```

## Kết luận

Vòng lặp và câu lệnh điều kiện là những cấu trúc điều khiển quan trọng trong Java. Chúng giúp chương trình có thể đưa ra quyết định và thực hiện các tác vụ lặp đi lặp lại một cách hiệu quả. Hãy thực hành nhiều để thành thạo các cấu trúc này!
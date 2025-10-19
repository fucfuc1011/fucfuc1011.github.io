---
title: "Collections Framework trong Java"
date: 2022-10-05
category: "Java"
image: "/images/posts/java-collections.jpg"

---

## Collections Framework là gì?

Collections Framework là một kiến trúc thống nhất để lưu trữ và thao tác với nhóm các object. Nó cung cấp các interface và class để xử lý các tập hợp dữ liệu một cách hiệu quả.

## Các loại Collection chính

### 1. ArrayList

ArrayList là một mảng động, có thể thay đổi kích thước.

```java
import java.util.ArrayList;

public class ArrayListExample {
    public static void main(String[] args) {
        // Tạo ArrayList
        ArrayList<String> danhSach = new ArrayList<>();
        
        // Thêm phần tử
        danhSach.add("Java");
        danhSach.add("Python");
        danhSach.add("JavaScript");
        
        // Truy cập phần tử
        System.out.println("Phần tử đầu tiên: " + danhSach.get(0));
        
        // Kích thước
        System.out.println("Số phần tử: " + danhSach.size());
        
        // Duyệt ArrayList
        for (String ngonNgu : danhSach) {
            System.out.println(ngonNgu);
        }
        
        // Xóa phần tử
        danhSach.remove("Python");
        
        // Kiểm tra tồn tại
        if (danhSach.contains("Java")) {
            System.out.println("Java có trong danh sách");
        }
    }
}
```

### 2. LinkedList

LinkedList lưu trữ dữ liệu dưới dạng danh sách liên kết.

```java
import java.util.LinkedList;

public class LinkedListExample {
    public static void main(String[] args) {
        LinkedList<Integer> numbers = new LinkedList<>();
        
        // Thêm vào cuối
        numbers.add(10);
        numbers.add(20);
        numbers.add(30);
        
        // Thêm vào đầu
        numbers.addFirst(5);
        
        // Thêm vào cuối
        numbers.addLast(40);
        
        System.out.println(numbers); // [5, 10, 20, 30, 40]
        
        // Lấy và xóa phần tử đầu
        int first = numbers.removeFirst();
        System.out.println("Phần tử đầu: " + first);
        
        // Lấy và xóa phần tử cuối
        int last = numbers.removeLast();
        System.out.println("Phần tử cuối: " + last);
    }
}
```

### 3. HashSet

HashSet lưu trữ các phần tử duy nhất, không có thứ tự.

```java
import java.util.HashSet;

public class HashSetExample {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>();
        
        // Thêm phần tử
        set.add("Apple");
        set.add("Banana");
        set.add("Orange");
        set.add("Apple"); // Không thêm được vì trùng
        
        System.out.println(set); // [Orange, Apple, Banana]
        System.out.println("Số phần tử: " + set.size()); // 3
        
        // Kiểm tra tồn tại
        if (set.contains("Apple")) {
            System.out.println("Có Apple trong set");
        }
        
        // Xóa phần tử
        set.remove("Banana");
        
        // Duyệt set
        for (String item : set) {
            System.out.println(item);
        }
    }
}
```

### 4. HashMap

HashMap lưu trữ dữ liệu dưới dạng key-value (khóa-giá trị).

```java
import java.util.HashMap;

public class HashMapExample {
    public static void main(String[] args) {
        // Tạo HashMap: <Mã SV, Tên SV>
        HashMap<String, String> sinhVien = new HashMap<>();
        
        // Thêm phần tử
        sinhVien.put("SV001", "Nguyễn Văn An");
        sinhVien.put("SV002", "Trần Thị Bình");
        sinhVien.put("SV003", "Lê Văn Cường");
        
        // Truy cập giá trị theo key
        System.out.println("SV001: " + sinhVien.get("SV001"));
        
        // Kiểm tra key tồn tại
        if (sinhVien.containsKey("SV002")) {
            System.out.println("Tìm thấy SV002");
        }
        
        // Kiểm tra value tồn tại
        if (sinhVien.containsValue("Lê Văn Cường")) {
            System.out.println("Có sinh viên tên Lê Văn Cường");
        }
        
        // Duyệt HashMap
        for (String key : sinhVien.keySet()) {
            System.out.println(key + ": " + sinhVien.get(key));
        }
        
        // Xóa phần tử
        sinhVien.remove("SV002");
        
        // Số phần tử
        System.out.println("Số sinh viên: " + sinhVien.size());
    }
}
```

## So sánh ArrayList vs LinkedList

| Đặc điểm | ArrayList | LinkedList |
|----------|-----------|------------|
| Truy cập phần tử | Nhanh O(1) | Chậm O(n) |
| Thêm/xóa đầu cuối | Chậm | Nhanh |
| Bộ nhớ | Ít hơn | Nhiều hơn |
| Sử dụng khi | Truy cập nhiều | Thêm/xóa nhiều |

## Ví dụ thực tế: Quản lý Sản phẩm

```java
import java.util.*;

class SanPham {
    private String ma;
    private String ten;
    private double gia;
    
    public SanPham(String ma, String ten, double gia) {
        this.ma = ma;
        this.ten = ten;
        this.gia = gia;
    }
    
    public String getMa() { return ma; }
    public String getTen() { return ten; }
    public double getGia() { return gia; }
    
    @Override
    public String toString() {
        return "Mã: " + ma + ", Tên: " + ten + ", Giá: " + gia + " VNĐ";
    }
}

public class QuanLySanPham {
    public static void main(String[] args) {
        // Sử dụng ArrayList để lưu danh sách sản phẩm
        ArrayList<SanPham> danhSach = new ArrayList<>();
        
        // Thêm sản phẩm
        danhSach.add(new SanPham("SP001", "Laptop Dell", 15000000));
        danhSach.add(new SanPham("SP002", "iPhone 15", 25000000));
        danhSach.add(new SanPham("SP003", "Samsung Galaxy", 18000000));
        
        // Hiển thị danh sách
        System.out.println("=== DANH SÁCH SẢN PHẨM ===");
        for (SanPham sp : danhSach) {
            System.out.println(sp);
        }
        
        // Sử dụng HashMap để lưu theo mã sản phẩm
        HashMap<String, SanPham> khoSanPham = new HashMap<>();
        for (SanPham sp : danhSach) {
            khoSanPham.put(sp.getMa(), sp);
        }
        
        // Tìm sản phẩm theo mã
        String maCanTim = "SP002";
        if (khoSanPham.containsKey(maCanTim)) {
            System.out.println("\nTìm thấy: " + khoSanPham.get(maCanTim));
        }
        
        // Tính tổng giá trị kho
        double tongGiaTri = 0;
        for (SanPham sp : danhSach) {
            tongGiaTri += sp.getGia();
        }
        System.out.println("\nTổng giá trị kho: " + tongGiaTri + " VNĐ");
    }
}
```

## Các phương thức quan trọng

### ArrayList/LinkedList:
- `add(element)` - Thêm phần tử
- `get(index)` - Lấy phần tử tại vị trí
- `remove(index/object)` - Xóa phần tử
- `size()` - Lấy kích thước
- `clear()` - Xóa tất cả
- `contains(object)` - Kiểm tra tồn tại
- `isEmpty()` - Kiểm tra rỗng

### HashSet:
- `add(element)` - Thêm phần tử
- `remove(object)` - Xóa phần tử
- `contains(object)` - Kiểm tra tồn tại
- `size()` - Lấy kích thước
- `clear()` - Xóa tất cả

### HashMap:
- `put(key, value)` - Thêm cặp key-value
- `get(key)` - Lấy value theo key
- `remove(key)` - Xóa theo key
- `containsKey(key)` - Kiểm tra key tồn tại
- `containsValue(value)` - Kiểm tra value tồn tại
- `keySet()` - Lấy tập hợp các key
- `values()` - Lấy tập hợp các value
- `size()` - Lấy kích thước

## Sắp xếp Collection

```java
import java.util.*;

public class SortExample {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(50);
        numbers.add(20);
        numbers.add(80);
        numbers.add(10);
        
        // Sắp xếp tăng dần
        Collections.sort(numbers);
        System.out.println("Tăng dần: " + numbers);
        
        // Sắp xếp giảm dần
        Collections.sort(numbers, Collections.reverseOrder());
        System.out.println("Giảm dần: " + numbers);
        
        // Sắp xếp String
        ArrayList<String> names = new ArrayList<>();
        names.add("Cường");
        names.add("An");
        names.add("Bình");
        
        Collections.sort(names);
        System.out.println("Tên theo ABC: " + names);
    }
}
```

## Kết luận

Collections Framework là một phần quan trọng trong Java, giúp quản lý và thao tác với nhóm dữ liệu một cách hiệu quả. Việc chọn đúng loại Collection (ArrayList, LinkedList, HashSet, HashMap) tùy thuộc vào yêu cầu cụ thể của bài toán. Hãy thực hành nhiều để thành thạo các Collection này!
---
title: "Lập trình hướng đối tượng: Class và Object trong Java"
date: 2023-10-04
category: "Java"
image: "/images/posts/java-oop-class-object.jpg"
---

## Lập trình hướng đối tượng (OOP) là gì?

OOP (Object-Oriented Programming) là một phương pháp lập trình dựa trên khái niệm về các đối tượng (objects) và lớp (classes). Mỗi đối tượng có:
- **Thuộc tính (Attributes)**: Đặc điểm, tính chất
- **Phương thức (Methods)**: Hành vi, chức năng

## Class và Object

### Class (Lớp)

Class là bản thiết kế hoặc khuôn mẫu để tạo ra các object.

```java
public class SinhVien {
    // Thuộc tính (Attributes)
    String ten;
    int tuoi;
    String maSV;
    double diemTB;
    
    // Phương thức (Methods)
    void hienThiThongTin() {
        System.out.println("Tên: " + ten);
        System.out.println("Tuổi: " + tuoi);
        System.out.println("Mã SV: " + maSV);
        System.out.println("Điểm TB: " + diemTB);
    }
    
    void hoc() {
        System.out.println(ten + " đang học bài");
    }
}
```

### Object (Đối tượng)

Object là thể hiện cụ thể của một class.

```java
public class Main {
    public static void main(String[] args) {
        // Tạo object từ class SinhVien
        SinhVien sv1 = new SinhVien();
        
        // Gán giá trị cho thuộc tính
        sv1.ten = "Nguyễn Văn An";
        sv1.tuoi = 20;
        sv1.maSV = "SV001";
        sv1.diemTB = 8.5;
        
        // Gọi phương thức
        sv1.hienThiThongTin();
        sv1.hoc();
    }
}
```

## Constructor (Hàm khởi tạo)

Constructor là phương thức đặc biệt được gọi khi tạo object.

### Constructor mặc định:

```java
public class SinhVien {
    String ten;
    int tuoi;
    
    // Constructor mặc định
    public SinhVien() {
        ten = "Chưa có tên";
        tuoi = 0;
    }
}
```

### Constructor có tham số:

```java
public class SinhVien {
    String ten;
    int tuoi;
    String maSV;
    double diemTB;
    
    // Constructor có tham số
    public SinhVien(String ten, int tuoi, String maSV, double diemTB) {
        this.ten = ten;
        this.tuoi = tuoi;
        this.maSV = maSV;
        this.diemTB = diemTB;
    }
    
    void hienThiThongTin() {
        System.out.println("Tên: " + ten);
        System.out.println("Tuổi: " + tuoi);
        System.out.println("Mã SV: " + maSV);
        System.out.println("Điểm TB: " + diemTB);
    }
}

// Sử dụng
public class Main {
    public static void main(String[] args) {
        SinhVien sv1 = new SinhVien("Trần Thị Bình", 21, "SV002", 9.0);
        sv1.hienThiThongTin();
    }
}
```

## Từ khóa this

`this` đại diện cho object hiện tại.

```java
public class HinhChuNhat {
    double chieuDai;
    double chieuRong;
    
    public HinhChuNhat(double chieuDai, double chieuRong) {
        this.chieuDai = chieuDai;  // this.chieuDai là thuộc tính
        this.chieuRong = chieuRong; // chieuRong là tham số
    }
    
    double tinhDienTich() {
        return this.chieuDai * this.chieuRong;
    }
    
    double tinhChuVi() {
        return 2 * (this.chieuDai + this.chieuRong);
    }
}
```

## Access Modifiers (Phạm vi truy cập)

Java có 4 loại access modifiers:

| Modifier | Trong class | Trong package | Ngoài package (subclass) | Mọi nơi |
|----------|------------|---------------|-------------------------|---------|
| private | ✓ | ✗ | ✗ | ✗ |
| default | ✓ | ✓ | ✗ | ✗ |
| protected | ✓ | ✓ | ✓ | ✗ |
| public | ✓ | ✓ | ✓ | ✓ |

```java
public class Person {
    private String name;      // Chỉ truy cập trong class
    public int age;           // Truy cập mọi nơi
    protected String address; // Truy cập trong package và subclass
    String phone;            // default - Truy cập trong package
}
```

## Getter và Setter

Để truy cập thuộc tính private, ta dùng getter và setter:

```java
public class NhanVien {
    private String ten;
    private double luong;
    
    // Constructor
    public NhanVien(String ten, double luong) {
        this.ten = ten;
        this.luong = luong;
    }
    
    // Getter cho ten
    public String getTen() {
        return ten;
    }
    
    // Setter cho ten
    public void setTen(String ten) {
        this.ten = ten;
    }
    
    // Getter cho luong
    public double getLuong() {
        return luong;
    }
    
    // Setter cho luong (có validation)
    public void setLuong(double luong) {
        if (luong > 0) {
            this.luong = luong;
        } else {
            System.out.println("Lương phải lớn hơn 0!");
        }
    }
    
    public void hienThiThongTin() {
        System.out.println("Tên: " + ten);
        System.out.println("Lương: " + luong);
    }
}

// Sử dụng
public class Main {
    public static void main(String[] args) {
        NhanVien nv = new NhanVien("Lê Văn Cường", 15000000);
        
        System.out.println("Lương hiện tại: " + nv.getLuong());
        
        // Thay đổi lương
        nv.setLuong(18000000);
        System.out.println("Lương mới: " + nv.getLuong());
    }
}
```

## Ví dụ thực tế: Quản lý Tài khoản ngân hàng

```java
public class TaiKhoanNganHang {
    private String soTaiKhoan;
    private String chuTaiKhoan;
    private double soDu;
    
    // Constructor
    public TaiKhoanNganHang(String soTaiKhoan, String chuTaiKhoan) {
        this.soTaiKhoan = soTaiKhoan;
        this.chuTaiKhoan = chuTaiKhoan;
        this.soDu = 0;
    }
    
    // Nạp tiền
    public void napTien(double soTien) {
        if (soTien > 0) {
            soDu += soTien;
            System.out.println("Nạp thành công " + soTien + " VNĐ");
        } else {
            System.out.println("Số tiền không hợp lệ!");
        }
    }
    
    // Rút tiền
    public void rutTien(double soTien) {
        if (soTien > 0 && soTien <= soDu) {
            soDu -= soTien;
            System.out.println("Rút thành công " + soTien + " VNĐ");
        } else {
            System.out.println("Không đủ số dư hoặc số tiền không hợp lệ!");
        }
    }
    
    // Kiểm tra số dư
    public void kiemTraSoDu() {
        System.out.println("Số dư hiện tại: " + soDu + " VNĐ");
    }
    
    // Getter
    public String getSoTaiKhoan() {
        return soTaiKhoan;
    }
    
    public String getChuTaiKhoan() {
        return chuTaiKhoan;
    }
    
    public double getSoDu() {
        return soDu;
    }
}

// Sử dụng
public class Main {
    public static void main(String[] args) {
        TaiKhoanNganHang tk = new TaiKhoanNganHang("0123456789", "Phạm Thành Phúc");
        
        tk.napTien(5000000);
        tk.kiemTraSoDu();
        
        tk.rutTien(2000000);
        tk.kiemTraSoDu();
        
        tk.rutTien(4000000); // Không đủ tiền
    }
}
```

## 4 Tính chất của OOP

### 1. Encapsulation (Đóng gói)
Che giấu thông tin bên trong object, chỉ cho phép truy cập thông qua các phương thức public.

### 2. Inheritance (Kế thừa)
Class con có thể kế thừa thuộc tính và phương thức của class cha.

### 3. Polymorphism (Đa hình)
Một phương thức có thể có nhiều hình thức khác nhau.

### 4. Abstraction (Trừu tượng)
Che giấu chi tiết phức tạp, chỉ hiển thị những gì cần thiết.

## Kết luận

Class và Object là nền tảng của lập trình hướng đối tượng trong Java. Việc hiểu rõ cách tạo và sử dụng class, object, constructor, và các access modifiers sẽ giúp bạn xây dựng các chương trình Java mạnh mẽ và dễ bảo trì. Trong bài viết tiếp theo, chúng ta sẽ tìm hiểu về Collections Framework trong Java!
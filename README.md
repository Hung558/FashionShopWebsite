# 👗 Fashion Shop Management (FSM) 🛍️

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.7-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Java](https://img.shields.io/badge/Java-17-orange.svg)](https://www.oracle.com/java/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-blue.svg)](https://www.mysql.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**Fashion Shop Management** là một nền tảng thương mại điện tử hiện đại, chuyên nghiệp dành cho các cửa hàng thời trang. Hệ thống được xây dựng trên nền tảng Spring Boot 3 mạnh mẽ, cung cấp trải nghiệm mua sắm mượt mà cho khách hàng và công cụ quản trị toàn diện cho doanh nghiệp.

---

## 📖 Mục lục
- [Tổng quan hệ thống](#-tổng-quan-hệ-thống)
- [Tổng quan chức năng](#-tổng-quan-chức-năng)
- [Vai trò người dùng](#-vai-trò-người-dùng)
- [Tech Stack](#-tech-stack)
- [Cấu trúc dự án](#-cấu-trúc-dự-án)
- [Cài đặt & Chạy](#-cài-đặt--chạy)
- [Tính năng & Màn hình](#-tính-năng--màn-hình)

---

## 🌟 Tổng quan hệ thống
Hệ thống FSM không chỉ đơn thuần là một website bán hàng, mà là một giải pháp quản lý kinh doanh thời trang khép kín từ khâu nhập sản phẩm, quản lý kho (biến thể sản phẩm), đến quy trình đặt hàng, thanh toán trực tuyến và chăm sóc khách hàng qua Blog & Support.

---

## 🚀 Tổng quan chức năng

### 👤 Khách hàng (Customer)
- **Xác thực đa năng**: Đăng ký/Đăng nhập truyền thống hoặc qua Google/Facebook (OAuth2).
- **Mua sắm thông minh**: Tìm kiếm, lọc sản phẩm theo danh mục, thương hiệu, giá cả.
- **Biến thể sản phẩm**: Chọn kích thước (Size), màu sắc (Color), chất liệu một cách trực quan.
- **Giỏ hàng & Yêu thích**: Quản lý giỏ hàng realtime, lưu sản phẩm yêu thích (Wishlist).
- **Thanh toán**: Tích hợp cổng thanh toán trực tuyến **VNPay**, hỗ trợ thanh toán an toàn.
- **Theo dõi đơn hàng**: Kiểm tra trạng thái đơn hàng (Pending, Paid, Shipped, Cancelled).
- **Cá nhân hóa**: Quản lý hồ sơ, địa chỉ mặc định, lịch sử mua hàng.

### 🛡️ Quản trị viên & Nhân viên (Admin/Staff)
- **Dashboard**: Thống kê doanh thu, đơn hàng và hoạt động hệ thống.
- **Quản lý sản phẩm**: CRUD sản phẩm, danh mục, thương hiệu và hình ảnh.
- **Quản lý kho**: Theo dõi tồn kho theo từng biến thể (SKU).
- **Quản lý đơn hàng**: Xác nhận, cập nhật trạng thái vận chuyển và xử lý hoàn tiền.
- **Quản trị nội dung**: Viết và quản lý Blog thời trang, phản hồi tin nhắn từ khách hàng.
- **Audit Logs**: Lưu vết mọi hành động nhạy cảm trên hệ thống để đảm bảo an ninh.

---

## 👥 Vai trò người dùng (Roles)

| Vai trò | Mô tả | Quyền hạn chính |
| :--- | :--- | :--- |
| **Guest** | Khách truy cập | Xem sản phẩm, đọc Blog, tìm kiếm. |
| **Customer** | Khách hàng | Mua hàng, thanh toán, Wishlist, theo dõi đơn hàng, Profile. |
| **Staff** | Nhân viên | Quản lý Blog, cập nhật trạng thái đơn hàng, hỗ trợ khách hàng. |
| **Admin** | Quản trị viên | Toàn quyền hệ thống: Quản lý User, Product, Order, Audit Logs. |

---

## 🛠️ Tech Stack

### Backend
- **Core**: Java 17, Spring Boot 3.5.7
- **Security**: Spring Security 6 (OAuth2 Client & Server)
- **Database**: MySQL 8.0
- **Persistence**: Spring Data JPA (Hibernate)
- **Communication**: Spring Boot Mail (SMTP)
- **Utilities**: Lombok, Spring Session JDBC, Validation

### Frontend
- **Engine**: Thymeleaf Template Engine
- **Styling**: HTML5, CSS3, JavaScript (Vanilla Custom & UI Frameworks)
- **Features**: Responsive Design, Real-time Cart updates.

---

## 📂 Cấu trúc dự án
```text
Fashion-Shop-Management/
├── src/main/java/org/fsm/
│   ├── config/          # Cấu hình Security, VNPay, MVC
│   ├── controller/      # Xử lý Request (Admin, Staff, Public, API)
│   ├── dto/             # Đối tượng chuyển đổi dữ liệu
│   ├── entity/          # Bản đồ cơ sở dữ liệu (Database Entities)
│   ├── repository/      # Giao tiếp cơ sở dữ liệu
│   ├── service/         # Logic nghiệp vụ (Business Logic)
│   ├── security/        # Custom Authentication & OAuth2 Handlers
│   └── utils/           # Công cụ hỗ trợ (Helper classes)
├── src/main/resources/
│   ├── templates/       # Giao diện Thymeleaf (.html)
│   ├── static/          # Assets: CSS, JS, Images
│   └── application.properties # Cấu hình hệ thống
└── fsm_query_mysql.sql  # Script khởi tạo cơ sở dữ liệu
```

---

## ⚙️ Cài đặt & Chạy

### 1. Chuẩn bị
- Đã cài đặt **JDK 17** và **Maven**.
- Đã cài đặt **MySQL Server** (Khuyên dùng v8.0+).

### 2. Thiết lập Cơ sở dữ liệu
- Tạo database mới: `CREATE DATABASE FashionShopManagement;`
- Chạy file `fsm_query_mysql.sql` để khởi tạo bảng và dữ liệu mẫu.

### 3. Cấu hình Ứng dụng
Mở file `src/main/resources/application.properties` và cập nhật thông tin:
```properties
spring.datasource.username=your_username
spring.datasource.password=your_password
# Cấu hình VNPay & Google OAuth2 nếu cần (đã có sẵn demo trong file)
```

### 4. Chạy ứng dụng
Sử dụng terminal tại thư mục gốc:
```bash
mvn spring-boot:run
```
Truy cập tại: `http://localhost:8080/fashionshop`

---

## 📱 Tính năng & Màn hình

- **Trang chủ**: Banner lôi cuốn, sản phẩm mới nhất & sản phẩm nổi bật.
- **Cửa hàng (Shop)**: Bộ lọc thông minh theo danh mục, màu sắc, size.
- **Chi tiết sản phẩm**: Gallery ảnh, chọn biến thể, mô tả chi tiết & đánh giá.
- **Blog**: Chia sẻ xu hướng thời trang, bài viết trình bày đẹp mắt.
- **Admin Dashboard**: Giao diện quản trị hiện đại, trực quan với đầy đủ biểu đồ và bảng dữ liệu.

---

> [!TIP]
> **Tài khoản mặc định (Sau khi chạy SQL):**
> Vui lòng kiểm tra bảng `users` trong database để xem danh sách tài khoản đã khởi tạo hoặc sử dụng tính năng Đăng ký mới.

---
*Phát triển bởi Đội ngũ FSM © 2026*

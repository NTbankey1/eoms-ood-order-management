
# EOMS – Object-Oriented Order Management System

## Phân tích cấu trúc nghiệp vụ và thiết kế lớp hướng đối tượng

Dự án thực hiện phân tích nghiệp vụ và thiết kế hướng đối tượng cho một hệ thống quản lý đơn hàng bán hàng.

## Mục tiêu

- Phân tích các khái niệm nghiệp vụ chính.
- Xây dựng Domain Model.
- Xác định trách nhiệm của các lớp.
- Thiết kế Design Class Diagram.
- Phân bổ trách nhiệm giữa Entity và Service.
- Phân tích và so sánh các phương án thiết kế.
- Mô phỏng quy trình đặt hàng từ lúc tạo đơn đến kiểm tra tồn kho và thanh toán.

## Thành viên

- Lê Ngô Kỳ Vọng
- Nguyễn Thái Bảo
- Dương Vĩ Tín
- Khang
- Từ Đăng Khoa

## Phạm vi hệ thống

Các đối tượng nghiệp vụ chính:

- Customer
- Order
- OrderLine
- Product

Các service chính:

- OrderService
- InventoryService
- PaymentService

## Kiến trúc thiết kế

```text
Customer
   │
   │ 1
   ▼
Order
   │
   │ 1..*
   ▼
OrderLine
   │
   │ *
   ▼
Product
```

Các service chịu trách nhiệm điều phối nghiệp vụ:

```text
OrderService
     │
     ├── InventoryService
     │
     └── PaymentService
```

## Quy trình đặt hàng

```text
Customer
   │
   ▼
OrderService.placeOrder()
   │
   ├── Create Order
   ├── Add OrderLine
   ├── Check Inventory
   ├── Reserve Stock
   ├── Process Payment
   │
   ├── Success → CONFIRMED
   │
   └── Failure → CANCELLED
```

## Nội dung chính

1. Phân tích nghiệp vụ
2. Business Rules
3. Domain Model
4. Responsibility Assignment
5. Design Class Diagram
6. Domain Model → Design Classes
7. So sánh phương án thiết kế
8. Quy trình `placeOrder`
9. Peer Review
10. Kết luận và thuyết trình

## Công nghệ / Công cụ

- UML
- Object-Oriented Design
- Class Diagram
- Domain Modeling
- Git / GitHub

## Mục tiêu học tập

Thông qua dự án, nhóm áp dụng các nguyên tắc phân tích và thiết kế hướng đối tượng để chuyển từ yêu cầu nghiệp vụ thành một thiết kế lớp có trách nhiệm rõ ràng, dễ hiểu và có khả năng mở rộng.a

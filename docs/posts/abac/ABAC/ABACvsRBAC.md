---
title: abac-vs-rbac
nav_tile: abac-vs-rbac
draft: true 
comments: true
date: 2024-12-19
categories:
  - abac
---
# So sánh ABAC và RBAC: Lựa chọn phù hợp cho kiểm soát truy cập

Mô hình kiểm soát truy cập dựa trên vai trò (RBAC) và dựa trên thuộc tính (ABAC) là hai phương pháp phổ biến trong quản lý truy cập. Việc lựa chọn giữa hai mô hình này phụ thuộc vào yêu cầu bảo mật, độ phức tạp và khả năng mở rộng của tổ chức.

---

## **1. Điểm khác biệt chính**

ABAC xác định quyền truy cập dựa trên thuộc tính (người dùng, tài nguyên, môi trường), trong khi RBAC dựa trên vai trò được gán cho người dùng.

### **Bảng so sánh ABAC và RBAC**

| **Đặc điểm**         | **ABAC**                                                     | **RBAC**                                      |
|----------------------|-------------------------------------------------------------|-----------------------------------------------|
| **Cơ sở xác định**   | Thuộc tính (người dùng, tài nguyên, môi trường)             | Vai trò được gán cho người dùng               |
| **Độ chi tiết**      | **Cao**: Kiểm soát truy cập ở mức tinh tế và linh hoạt      | **Thấp hơn**: Kiểm soát giới hạn ở mức vai trò|
| **Khả năng mở rộng** | **Dễ dàng mở rộng**: Thêm thuộc tính, chính sách linh hoạt  | **Hạn chế**: Thêm vai trò cần cấu hình lại    |
| **Quản lý**          | **Đơn giản hơn**: Tập trung vào chính sách, ít vai trò cố định| **Phức tạp hơn**: Quản lý nhiều vai trò và quyền|
| **Khả năng kiểm soát**| **Linh hoạt và chính xác hơn**                              | **Giới hạn** ở mức vai trò                    |

---

## **2. Ưu điểm của ABAC so với RBAC**

### **Linh hoạt**
- ABAC cho phép xác định chính sách dựa trên nhiều thuộc tính khác nhau (ví dụ: thời gian, vị trí, trạng thái của tài nguyên), tạo ra sự linh hoạt vượt trội.

### **Kiểm soát chi tiết**
- Kiểm soát truy cập ở mức độ chính xác, cho phép quản lý các trường hợp phức tạp và giảm thiểu nguy cơ truy cập trái phép.

### **Mở rộng**
- Hệ thống ABAC có thể dễ dàng mở rộng khi thêm người dùng, tài nguyên hoặc chính sách mới, mà không cần cấu hình lại vai trò cố định như trong RBAC.

### **Quản lý đơn giản hơn**
- Với ABAC, việc quản lý tập trung vào chính sách dựa trên thuộc tính, giảm bớt sự phức tạp trong việc gán vai trò và quyền cho từng người dùng.

---

## **3. Nhược điểm của ABAC**

### **Phức tạp trong triển khai**
- Việc xác định và cấu hình các thuộc tính cũng như chính sách có thể phức tạp, đặc biệt đối với các tổ chức chưa quen thuộc với mô hình này.

### **Tài nguyên tính toán**
- ABAC đòi hỏi nhiều tài nguyên tính toán hơn để đánh giá chính sách, đặc biệt khi số lượng thuộc tính và quy tắc lớn.

---

## **4. Khi nào nên chọn ABAC hoặc RBAC?**

| **Tiêu chí**                                | **ABAC**                                            | **RBAC**                                        |
|---------------------------------------------|----------------------------------------------------|------------------------------------------------|
| **Yêu cầu kiểm soát phức tạp**              | Phù hợp: Kiểm soát truy cập dựa trên nhiều yếu tố | Không phù hợp                                  |
| **Hệ thống có quy mô lớn, nhiều biến động** | Dễ dàng mở rộng, phù hợp với nhu cầu thay đổi    | Hạn chế do cần cấu hình lại vai trò           |
| **Đơn giản hóa quản lý**                    | Quản lý chính sách trực tiếp qua thuộc tính      | Quản lý phức tạp với nhiều vai trò và quyền   |
| **Hiệu suất hệ thống**                      | Yêu cầu cao hơn, cần tối ưu                      | Yêu cầu thấp hơn                              |

---

## **5. Kết luận**

ABAC và RBAC đều có những điểm mạnh riêng:

- **RBAC**: Lý tưởng cho các hệ thống nhỏ, ít phức tạp và ít biến động.

- **ABAC**: Lựa chọn tối ưu cho các tổ chức lớn, yêu cầu kiểm soát linh hoạt, chi tiết, và khả năng mở rộng.

Sự lựa chọn giữa hai mô hình này cần dựa trên:

- Nhu cầu kiểm soát truy cập.

- Quy mô và tính phức tạp của hệ thống.

- Nguồn lực triển khai và quản lý.

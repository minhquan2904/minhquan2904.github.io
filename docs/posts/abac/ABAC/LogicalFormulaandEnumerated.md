---
title: abac-logic-formulavsenum
nav_tile: abac-logic-formulavsenum
draft: true 
comments: true
date: 2024-06-04
categories:
  - abac
---
# Mô hình chính sách ABAC: Logic-Formula và Liệt kê
Bài viết này giới thiệu hai kỹ thuật phổ biến để biểu diễn chính sách ABAC: Logic-Formula và Liệt kê.

## 1. Mô hình Logic-Formula:

Phương pháp: Xác định chính sách ủy quyền bằng cách sử dụng các công thức logic, bao gồm các mệnh đề được biểu diễn bằng các toán tử logic (ví dụ: AND, OR, ≥, ≠) trên 
các giá trị thuộc tính.

Ví dụ:

```sh
 can_access(s, a, o) -> role(s) = "doctor" AND ward(s) = ward(o) AND (a = read OR a = write)
```
Chính sách này cho phép các chủ thể có vai trò là bác sĩ đọc hoặc ghi vào bất kỳ đối tượng nào có cùng khoa với họ.

**Ưu điểm**:

- Biểu diễn chính sách một cách mạnh mẽ và hiệu quả.

- Cho phép xác định các yêu cầu kinh doanh phức tạp.

**Nhược điểm**:

- Khó kiểm tra chính sách hiệu quả.

- Yêu cầu gán giá trị thuộc tính cho tất cả các chủ thể và đối tượng trước khi kiểm tra.

## 2. Mô hình Liệt kê:

Phương pháp: Xác định chính sách bằng cách liệt kê các mối quan hệ giữa các tên thuộc tính.

Ví dụ:

- **NGAC**: Sử dụng các mối quan hệ chứa đựng, liên kết (uai, opsi, oai) để xác định quyền truy cập.

- **Kiểm soát truy cập dựa trên nhãn**: Sử dụng các nhãn để xác định quyền truy cập.

**Ưu điểm**:

- Hỗ trợ các thuật toán hiệu quả để kiểm tra chính sách cho từng người dùng và từng đối tượng.

**Nhược điểm**:

- Có thể phức tạp khi số lượng thuộc tính và mối quan hệ tăng lên.

**So sánh**:

- Logic-Formula: Mạnh mẽ và hiệu quả, nhưng khó kiểm tra.

- Liệt kê: Dễ kiểm tra, nhưng có thể phức tạp khi số lượng thuộc tính tăng lên.

**Kiểm tra chính sách**:

- Kiểm tra trước: Kiểm tra các khả năng (thao tác, đối tượng) của chủ thể và các mục nhập kiểm soát truy cập (chủ thể, thao tác) của đối tượng.

- Mô hình Liệt kê: Hỗ trợ các thuật toán hiệu quả để kiểm tra chính sách.

- Mô hình Logic-Formula: Khó kiểm tra hiệu quả.

Kết luận:

> Cả hai mô hình Logic-Formula và Liệt kê đều có ưu nhược điểm riêng. Lựa chọn mô hình phù hợp phụ thuộc vào yêu cầu cụ thể của hệ thống và ưu tiên về hiệu suất kiểm tra chính sách.
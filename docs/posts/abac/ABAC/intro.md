---
title: abac-intro
nav_tile: abac-intro
draft: true 
comments: true
date: 2024-06-04
categories:
  - abac
---

# Kiểm soát truy cập dựa trên thuộc tính (Attribute-Based Access Control - ABAC)

Bài viết này giới thiệu ABAC, một mô hình kiểm soát truy cập linh hoạt và mạnh mẽ, cho phép thiết lập chính sách dựa trên các thuộc tính của người dùng, đối tượng và môi trường.

Ưu điểm của ABAC:

- Linh hoạt: Dễ dàng thiết lập và sửa đổi chính sách dựa trên thuộc tính.

- Chính xác: Cho phép xác định chính xác quyền truy cập dựa trên nhiều thuộc tính.

- Nâng cao tính năng: Hỗ trợ nhiều quy tắc phức tạp hơn so với các mô hình truyền thống.

- Tự động hóa: Cho phép tự động hóa các quyết định về quyền truy cập.

- Xử lý người dùng ngoài: Hỗ trợ người dùng mới gia nhập mà không cần sửa đổi chính sách.

## Các khái niệm chính

- **Thuộc tính**: Các đặc điểm của người dùng, đối tượng và môi trường.

- **Chính sách**: Được xác định dựa trên các thuộc tính để xác định ai có thể thực hiện thao tác nào trên đối tượng nào.

- **Quy tắc**: Được sử dụng để xác định quyền truy cập dựa trên các thuộc tính.

- **Môi trường**: Bao gồm các thuộc tính liên quan đến ngữ cảnh của yêu cầu truy cập.

## Cách thức hoạt động:

- Gán thuộc tính: Gán thuộc tính cho người dùng, đối tượng và môi trường.

- Xây dựng chính sách: Xây dựng chính sách dựa trên các thuộc tính.

- Xác định quy tắc: Thiết lập quy tắc kiểm soát quyền truy cập dựa trên chính sách.

- Phân tích yêu cầu: Phân tích yêu cầu truy cập dựa trên thuộc tính.

- Quyết định: Cơ chế ABAC đưa ra quyết định cho phép hoặc từ chối quyền truy cập dựa trên các quy tắc.

Ví dụ:

- Một bác sĩ chuyên khoa tim có thể được phép truy cập vào hồ sơ bệnh nhân tim mạch.

- Một quản trị viên hệ thống có thể được phép truy cập vào các máy chủ trong giờ hành chính.

## Các thành phần chính

- Dữ liệu kiểm soát truy cập: Lưu trữ các thuộc tính và chính sách.

- Hoạt động quản trị: Cho phép cấu hình dữ liệu kiểm soát truy cập.

- Chức năng thực thi chính sách: Kiểm tra yêu cầu truy cập và áp dụng các quy tắc.

So sánh với các mô hình khác:

ABAC: Linh hoạt hơn, chính xác hơn và có khả năng tự động hóa cao hơn so với DAC và RBAC.

## Kết luận

> ABAC là một mô hình kiểm soát truy cập mạnh mẽ và linh hoạt, phù hợp với các hệ thống phân tán, động và có nhu cầu quản lý quyền truy cập phức tạp.
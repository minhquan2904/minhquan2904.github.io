---
title: abac-architecture
nav_tile: abac-architecture
draft: true 
date: 2024-06-04
categories:
  - abac
---
# Kiến trúc và thành phần chức năng của ABAC

Bài viết này thảo luận về hai kiến trúc phổ biến được sử dụng để triển khai ABAC: kiến trúc XACML và kiến trúc NGAC. Cả hai kiến trúc đều bao gồm bốn lớp chức năng và phân chia thông tin: thực thi, quyết định, dữ liệu kiểm soát truy cập và quản trị.

## Kiến trúc XACML:

Kiến trúc tham chiếu: Dựa trên tiêu chuẩn XACML (eXtensible Access Control Markup Language).

Thành phần:

- Điểm quyết định chính sách (PDP): Tính toán các quyết định cho phép hoặc từ chối yêu cầu truy cập.

- Điểm thực thi chính sách (PEP): Thực thi các quyết định của PDP.

- Xử lý ngữ cảnh: Chuyển đổi yêu cầu truy cập và phản hồi giữa các định dạng.

- Điểm thông tin chính sách (PIP): Lưu trữ thông tin về thuộc tính của người dùng, đối tượng và môi trường.

- Điểm truy xuất chính sách (PRP): Lưu trữ các chính sách và quy tắc.

- Điểm quản trị chính sách (PAP): Tạo và quản lý các chính sách và quy tắc.

- Điểm quản trị thuộc tính (AAP): Tạo và quản lý các thuộc tính của người dùng và đối tượng.

- Điểm truy cập tài nguyên (RAP): Thực hiện các thao tác trên tài nguyên.

## Kiến trúc NGAC:

Kiến trúc chức năng: Dựa trên tiêu chuẩn NGAC (Next Generation Access Control).

Thành phần:

- PEP: Bắt giữ các yêu cầu truy cập.

- PDP: Tính toán các quyết định về quyền truy cập.

- PIP: Lưu trữ các thuộc tính và mối quan hệ.

- PAP: Tạo và quản lý các thuộc tính và mối quan hệ.

- RAP: Thực hiện các thao tác trên tài nguyên.
- EPP: Xử lý các sự kiện và thay đổi trạng thái kiểm soát truy cập.

Sự khác biệt:

XACML: Tập trung vào việc xử lý các yêu cầu truy cập và phản hồi theo định dạng tiêu chuẩn.

NGAC: Tập trung vào việc quản lý các thuộc tính và mối quan hệ, hỗ trợ các thao tác quản trị và xử lý sự kiện.

Kết luận:

> Cả XACML và NGAC đều cung cấp kiến trúc để triển khai ABAC. Chọn kiến trúc phù hợp phụ thuộc vào yêu cầu cụ thể của hệ thống. XACML phù hợp cho các hệ thống cần xử lý các yêu cầu truy cập phức tạp, trong khi NGAC phù hợp cho các hệ thống cần quản lý các thuộc tính và mối quan hệ một cách linh hoạt.
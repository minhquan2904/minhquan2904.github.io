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

ABAC là một mô hình kiểm soát truy cập **sử dụng các thuộc tính của chủ thể (người yêu cầu truy cập), đối tượng (tài nguyên được yêu cầu truy cập) và môi trường (bối cảnh của yêu cầu)** để đưa ra quyết định về việc có cho phép truy cập hay không.

Ưu điểm của ABAC:

- Linh hoạt: Dễ dàng thiết lập và sửa đổi chính sách dựa trên thuộc tính.

- Chính xác: Cho phép xác định chính xác quyền truy cập dựa trên nhiều thuộc tính.

- Nâng cao tính năng: Hỗ trợ nhiều quy tắc phức tạp hơn so với các mô hình truyền thống.

- Tự động hóa: Cho phép tự động hóa các quyết định về quyền truy cập.

- Xử lý người dùng ngoài: Hỗ trợ người dùng mới gia nhập mà không cần sửa đổi chính sách.

## Các khái niệm chính

- **Thuộc tính**: cung cấp thông tin chi tiết về các thực thể tham gia vào quá trình kiểm soát truy cập, ví dụ: vai trò của người dùng, độ nhạy cảm của tài liệu, vị trí của thiết bị.

- **Quy tắc**: được xây dựng bằng cách sử dụng các thuộc tính này để xác định các điều kiện cần thiết cho việc truy cập. Ví dụ: "Chỉ những bác sĩ được chỉ định cho khoa nhi mới có thể truy cập hồ sơ bệnh án của bệnh nhân trong khoa nhi".

- **Chính sách**: là tập hợp các quy tắc ABAC được sử dụng để quản lý truy cập cho một hệ thống hoặc ứng dụng cụ thể.

- **Môi trường**: Bao gồm các thuộc tính liên quan đến ngữ cảnh của yêu cầu truy cập.

## Cách thức hoạt động:

- Gán thuộc tính: Gán thuộc tính cho người dùng, đối tượng và môi trường.

- Xây dựng chính sách: Xây dựng chính sách dựa trên các thuộc tính.

- Xác định quy tắc: Thiết lập quy tắc kiểm soát quyền truy cập dựa trên chính sách.

- Phân tích yêu cầu: Phân tích yêu cầu truy cập dựa trên thuộc tính.

- Quyết định: Cơ chế ABAC đưa ra quyết định cho phép hoặc từ chối quyền truy cập dựa trên các quy tắc.

Ví dụ tổng quát:

- Một bác sĩ chuyên khoa tim có thể được phép truy cập vào hồ sơ bệnh nhân tim mạch.

- Một quản trị viên hệ thống có thể được phép truy cập vào các máy chủ trong giờ hành chính.

Ví dụ chi tiết:

- **Chủ thể**: Bác sĩ (vai trò: bác sĩ, khoa: nhi)

- **Đối tượng**: Hồ sơ bệnh án (khoa: nhi)

- **Môi trường**: Thời gian truy cập (trong giờ làm việc)

- **Quy tắc**: Bác sĩ có vai trò là bác sĩ và được chỉ định cho khoa nhi có thể truy cập hồ sơ bệnh án của bệnh nhân trong khoa nhi trong giờ làm việc.

## Các thành phần chính

- Dữ liệu kiểm soát truy cập: Lưu trữ các thuộc tính và chính sách.

- Hoạt động quản trị: Cho phép cấu hình dữ liệu kiểm soát truy cập.

- Chức năng thực thi chính sách: Kiểm tra yêu cầu truy cập và áp dụng các quy tắc.

So sánh với các mô hình khác:


- **Linh hoạt và chi tiết**: ABAC cho phép xác định quyền truy cập dựa trên nhiều thuộc tính kết hợp, từ thuộc tính của người dùng, tài nguyên đến cả môi trường. Điều này cho phép quản trị viên thiết lập chính sách truy cập chi tiết, đáp ứng các yêu cầu phức tạp của doanh nghiệp. Ví dụ, thay vì chỉ cho phép "nhân viên" truy cập tệp X, ABAC cho phép quy định chi tiết hơn như "nhân viên thuộc dự án A, trong giờ hành chính, truy cập từ mạng nội bộ mới được phép đọc tệp X".

- **Khả năng mở rộng cao**:  Khi doanh nghiệp phát triển, nhu cầu về kiểm soát truy cập cũng thay đổi. ABAC dễ dàng thích nghi với những thay đổi này bằng cách thêm thuộc tính và quy tắc mới. Việc bổ sung này không ảnh hưởng đến các chính sách hiện có, giúp đơn giản hóa việc quản lý và bảo trì hệ thống.

- **Hỗ trợ người dùng bên ngoài**: ABAC rất hữu ích trong môi trường có nhiều người dùng bên ngoài, chẳng hạn như khách hàng, đối tác hoặc nhà cung cấp. ABAC cho phép cấp quyền truy cập cho người dùng này dựa trên thuộc tính của họ mà không cần phải tạo tài khoản riêng biệt.

- **Đơn giản hóa quản lý**: ABAC loại bỏ sự cần thiết phải quản lý danh sách kiểm soát truy cập (ACL) phức tạp hoặc cấu trúc vai trò (role) rườm rà. Quản trị viên có thể dễ dàng tạo, sửa đổi và quản lý chính sách ABAC thông qua giao diện trực quan và ngôn ngữ chính sách dễ hiểu.

- **Nâng cao khả năng kiểm toán**: ABAC giúp đơn giản hóa việc kiểm toán truy cập bằng cách cung cấp nhật ký chi tiết về các quyết định truy cập. Nhật ký này ghi lại thông tin về người dùng, tài nguyên, hành động và thuộc tính được sử dụng để ra quyết định, giúp dễ dàng theo dõi và phân tích hoạt động truy cập

- **Thúc đẩy chia sẻ thông tin an toàn**: ABAC hỗ trợ chia sẻ thông tin an toàn giữa các tổ chức khác nhau. Bằng cách sử dụng các thuộc tính chung, các tổ chức có thể xác định chính sách truy cập nhất quán và cho phép chia sẻ thông tin an toàn mà không ảnh hưởng đến bảo mật.

## Kết luận

> ABAC là một mô hình kiểm soát truy cập mạnh mẽ và linh hoạt, phù hợp với các hệ thống phân tán, động và có nhu cầu quản lý quyền truy cập phức tạp.
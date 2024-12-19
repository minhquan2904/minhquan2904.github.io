---
title: how-it-works
nav_tile: how-it-works
draft: true 
comments: true
date: 2024-12-19
categories:
  - abac
---
# Cách thức hoạt động của ABAC

## **Tổng quan**
ABAC (Attribute-Based Access Control) hoạt động dựa trên việc **đánh giá các thuộc tính** của các thực thể liên quan (người dùng, tài nguyên, môi trường) so với **các quy tắc được xác định trước trong chính sách**. Nếu các thuộc tính đáp ứng các điều kiện trong quy tắc, quyền truy cập sẽ được cấp. Ngược lại, yêu cầu truy cập sẽ bị từ chối.

---

## **Các bước hoạt động**

### 1. **Yêu cầu truy cập**
- Người dùng hoặc ứng dụng gửi yêu cầu truy cập vào một tài nguyên cụ thể.

### 2. **PEP tiếp nhận yêu cầu**

**PEP (Policy Enforcement Point)** thu thập các thuộc tính liên quan đến yêu cầu truy cập, bao gồm:

  - **Thuộc tính chủ thể (người dùng):** Ví dụ: vai trò, phòng ban, vị trí, chứng chỉ.

  - **Thuộc tính đối tượng (tài nguyên):** Ví dụ: loại tệp, độ nhạy cảm, chủ sở hữu.

  - **Thuộc tính môi trường:** Ví dụ: thời gian, địa điểm, mức độ đe dọa.

### 3. **PEP gửi yêu cầu đến PDP**
- **PEP** chuyển thông tin yêu cầu truy cập, bao gồm các thuộc tính đã thu thập, đến **PDP (Policy Decision Point)**.

### 4. **PDP đánh giá chính sách**
- **PDP** sử dụng các chính sách ABAC đã được cấu hình bởi **PAP (Policy Administration Point)** để đánh giá yêu cầu truy cập.
- **PDP** kiểm tra xem các thuộc tính có đáp ứng các điều kiện trong quy tắc của chính sách hay không.

### 5. **PDP đưa ra quyết định**

Dựa trên kết quả đánh giá, **PDP** đưa ra quyết định:

  - **Cho phép** yêu cầu truy cập.

  - **Từ chối** yêu cầu truy cập.

### 6. **PEP thực thi quyết định**

**PEP** nhận quyết định từ **PDP** và thực thi nó:

  - Nếu được phép, **PEP** cho phép truy cập tài nguyên.

  - Nếu bị từ chối, **PEP** chặn truy cập và thông báo cho người dùng.

### 7. **Ghi lại nhật ký**
- Hệ thống **ABAC** ghi lại nhật ký chi tiết về yêu cầu truy cập, quyết định và các thuộc tính được sử dụng trong quá trình đánh giá.
- Nhật ký này hỗ trợ kiểm tra và phân tích sau này.

---

## **Ví dụ minh họa**

### **Chính sách** 
- Nhân viên thuộc phòng marketing, truy cập từ mạng nội bộ, trong giờ hành chính, được phép đọc các tệp báo cáo marketing.

### **Yêu cầu truy cập**
- Một nhân viên marketing muốn truy cập một tệp báo cáo marketing từ máy tính của mình trong mạng nội bộ, vào lúc 10 giờ sáng.

### **Đánh giá**
- **Chủ thể:** Nhân viên thuộc phòng marketing.
- **Đối tượng:** Tệp báo cáo marketing.
- **Môi trường:** Truy cập từ mạng nội bộ, lúc 10 giờ sáng (giờ hành chính).

### **Kết quả**
- Các thuộc tính đáp ứng chính sách. Quyết định: **cho phép** truy cập.

---

## **Kết luận**

Cách thức hoạt động của **ABAC** dựa trên việc **đánh giá các thuộc tính so với chính sách** để đưa ra quyết định truy cập. Mô hình này mang lại:

- **Tính chi tiết:** Điều chỉnh quyền truy cập dựa trên nhiều thuộc tính.
- **Hiệu quả:** Phù hợp với các yêu cầu phức tạp.
- **An toàn:** Đảm bảo kiểm soát truy cập chặt chẽ.

ABAC là giải pháp kiểm soát truy cập hiện đại, đáp ứng tốt các yêu cầu của môi trường doanh nghiệp ngày nay.

---
title: abac-architecture
nav_tile: abac-architecture
draft: true 
comments: true
date: 2024-06-04
categories:
  - abac
---
# Kiến trúc và thành phần chức năng của ABAC

## Các thành phần chính của một hệ thống ABAC:

- **PEP (Policy Enforcement Point - Điểm Thực Thi Chính Sách)**: Đây là điểm tiếp xúc đầu tiên của yêu cầu truy cập. PEP nhận yêu cầu truy cập từ chủ thể và chịu trách nhiệm thu thập các thuộc tính cần thiết để đưa ra quyết định. PEP có thể được tích hợp vào các ứng dụng, dịch vụ hoặc thiết bị khác nhau. Ví dụ, PEP có thể được nhúng trong một máy chủ web để kiểm soát truy cập vào các trang web, hoặc trong một hệ thống quản lý cơ sở dữ liệu để kiểm soát truy cập vào dữ liệu.

- **PDP (Policy Decision Point - Bộ Quyết Định Chính Sách)**: PDP là "bộ não" của hệ thống ABAC. PDP nhận thông tin về yêu cầu truy cập từ PEP, bao gồm các thuộc tính của chủ thể, đối tượng và môi trường. Sau đó, PDP so sánh thông tin này với các chính sách ABAC đã được thiết lập để đưa ra quyết định cuối cùng là cho phép hoặc từ chối truy cập.

- **PAP (Policy Administration Point - Bộ Quản Lý Chính Sách)**: PAP là nơi quản trị viên tạo, sửa đổi và quản lý các chính sách ABAC. PAP cung cấp giao diện để quản trị viên xác định thuộc tính, quy tắc và chính sách. Ví dụ, NextLabs Control Center trong giải pháp ABAC của NextLabs là một ví dụ về PAP, cho phép quản trị viên xây dựng các thành phần chính sách và triển khai chúng.

- **PIP (Policy Information Point - Điểm Cung Cấp Thông Tin)**: PIP cung cấp thông tin về các thuộc tính cần thiết cho quá trình ra quyết định. PIP có thể truy xuất thuộc tính từ nhiều nguồn khác nhau, chẳng hạn như cơ sở dữ liệu người dùng, hệ thống quản lý danh tính hoặc các dịch vụ web. Các ví dụ về thuộc tính được sử dụng trong chính sách ABAC bao gồm vai trò của người dùng, độ nhạy cảm của đối tượng, vị trí của thiết bị, thời gian truy cập

## Ví dụ minh họa về cách các thành phần ABAC phối hợp với nhau

### Tình huống:
- Một nhân viên (*chủ thể*) muốn truy cập vào một tệp (*đối tượng*) chứa thông tin nhạy cảm.

### Quy trình:
1. **Yêu cầu truy cập**: Yêu cầu truy cập được gửi đến ***PEP*** (Policy Enforcement Point) được tích hợp trong hệ thống quản lý tệp.

2. **Thu thập thuộc tính**:  ***PEP*** thu thập các thuộc tính liên quan, chẳng hạn như:
     - Vai trò của nhân viên.
     - Phòng ban của nhân viên.
     - Thời gian truy cập.

3. **Gửi đến PDP**: ***PEP*** gửi các thuộc tính này đến ***PDP*** (Policy Decision Point).

4. **So sánh với chính sách**:  ***PDP*** so sánh các thuộc tính này với các chính sách ABAC đã được cấu hình bởi ***PAP*** (Policy Administration Point).

5. **Đưa ra quyết định**: Nếu các thuộc tính đáp ứng các điều kiện trong chính sách (ví dụ: nhân viên thuộc phòng ban được phép truy cập tệp và đang truy cập trong giờ làm việc), ***PDP*** sẽ cho phép truy cập.

6. **Thực thi quyết định**: Quyết định này được ***PEP*** thực thi, và nhân viên có thể truy cập tệp.

### Kết luận:

Các thành phần **PEP**, **PDP**, **PAP**, và **PIP** (Policy Information Point) đóng vai trò quan trọng trong việc đảm bảo hệ thống ABAC hoạt động hiệu quả. 

Sự phối hợp nhịp nhàng giữa các thành phần này cho phép kiểm soát truy cập dựa trên thuộc tính một cách: **Linh hoạt**, **Chi tiết**, **An toàn**.

Điều này đáp ứng nhu cầu ngày càng cao của các tổ chức và doanh nghiệp hiện đại.


## Các thành phần bổ sung trong hệ thống ABAC

Ngoài bốn thành phần chính của hệ thống ABAC (PEP, PDP, PAP và PIP), còn có một số thành phần bổ sung giúp tăng cường chức năng và khả năng mở rộng của hệ thống.

### 1. **Bộ xử lý ngữ cảnh (Context Handler)**
#### **Vai trò**:
  - Chuyển đổi yêu cầu truy cập và phản hồi giữa các định dạng khác nhau.
#### **Chức năng**:
  - Nhận yêu cầu truy cập từ **PEP** và chuyển đổi nó thành định dạng mà **PDP** có thể hiểu.
  - Nhận phản hồi từ **PDP** và chuyển đổi nó trở lại định dạng mà **PEP** có thể xử lý.
  - Có khả năng:
    - Thu thập thông tin thuộc tính từ **PIP**.
    - Thực hiện các tác vụ bắt buộc bổ sung.

---

### 2. **Điểm truy cập tài nguyên (Resource Access Point - RAP)**
#### **Vai trò**:
- Thực hiện các thao tác trên tài nguyên sau khi nhận được ủy quyền từ **PEP**.
#### **Chức năng**:   
  - PEP gửi lệnh cho **RAP** tương ứng với tài nguyên cần truy cập sau khi nhận được quyết định "cho phép" từ **PDP** (kèm theo URI của tài nguyên vật lý).  
  - **RAP** thực hiện thao tác trên tài nguyên, bao gồm:
    - Trả về dữ liệu.
    - Trả về thông tin trạng thái cho **PEP**. 
  - **RAP** chỉ cho phép **PEP** truy cập tài nguyên và không chấp nhận yêu cầu từ bất kỳ thành phần nào khác.

---

### Tóm lại:
- **Bộ xử lý ngữ cảnh** và **Điểm truy cập tài nguyên** là các thành phần bổ sung quan trọng giúp hệ thống ABAC hoạt động hiệu quả hơn.
- Chúng cung cấp các chức năng như xử lý dữ liệu đầu vào/đầu ra, đảm bảo tính nhất quán và tăng cường khả năng bảo mật trong quá trình truy cập tài nguyên.


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
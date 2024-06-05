---
title: Shellsort
nav_tile: Shellsort
draft: true 
date: 2024-05-06
categories:
  - sort
---

# Sắp xếp Shell (Shellsort): Một thuật toán sắp xếp hiệu quả

Sắp xếp Shell, còn được gọi là Shellsort, là một thuật toán sắp xếp so sánh cải tiến dựa trên sắp xếp chèn. Nó được Donald Shell phát minh vào năm 1959. Về cơ bản, Shellsort là một dạng tổng quát của sắp xếp chèn hoạt động hiệu quả hơn bằng cách so sánh các phần tử cách xa nhau.

## Cách hoạt động của Shellsort

1. **Chia mảng thành các dãy con:** Thay vì so sánh các phần tử liền kề như sắp xếp chèn, Shellsort chia mảng thành các dãy con dựa trên một khoảng cách (gap) nhất định. Khoảng cách này giảm dần theo từng lần lặp.

2. **Sắp xếp các dãy con:** Mỗi dãy con được sắp xếp độc lập sử dụng sắp xếp chèn. Do các phần tử trong dãy con cách xa nhau, việc di chuyển các phần tử sai vị trí về đúng vị trí của chúng sẽ nhanh hơn.

3. **Giảm khoảng cách:** Sau khi tất cả các dãy con được sắp xếp, khoảng cách được giảm xuống (thường là chia đôi) và quá trình lặp lại.
# Documentation

Web cá nhân.

## Các lệnh khi chạy

Tài liệu này sử dụng [MkDocs](https://www.mkdocs.org/) để thực hiện gen thành HTML từ cấu trúc file markdown.

Serve để preview website khi viết tài liệu

```
mkdocs serve
```

Build tài liệu thành site HTML tĩnh (thư mục sau khi build là `site`)

```
mkdocs build
```

Trường hợp chưa thể chạy các lệnh trên, bạn cần phải cài đặt python và các package qua pip:

1. Cài đặt [python và pip](https://www.python.org/downloads/)
2. Cài đặt mkdocs qua pip `pip install mkdocs`
3. Cài đặt thêm material theme `pip install mkdocs-material`
4. Cài đặt các ext của python `pip install pymdown-extensions`

Có thể đọc thêm tài liệu tại [MkDocs](https://www.mkdocs.org/) và [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
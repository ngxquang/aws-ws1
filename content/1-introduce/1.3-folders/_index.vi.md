---
title: "Cấu trúc thư mục sau khi cài đặt MySQL"
date: "r Sys.Date()"
weight: 1
chapter: false
pre: " <b> 1.1 </b> "
---

- Cấu trúc thư mục được tổ chức như sau:

  1. **sys directory**: Chứa thông tin liên quan đến sys schema
  2. **performance_schema directory**: Lưu thông tin để kiểm tra hoạt động của MySQL lúc đang hoạt động
  3. **mysql directory**: Thông tin liên quan đến data dictionary và system tables. Các thông tin này được yêu cầu bởi MySQL khi hoạt động

  ![dir](/images/1.introduce/005-dir.png)
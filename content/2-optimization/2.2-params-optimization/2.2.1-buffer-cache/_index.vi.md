---
title: "Buffer_cache_hit"
date: "r Sys.Date()"
weight: 1
chapter: false
pre: " <b> 2.2.1 </b> "
---

- Tỷ lệ **buffer_cache_hit** cho biết việc sử dụng bộ nhớ của MySQL.
- Tỷ lệ này thể hiện các yêu cầu được gửi đến thì MySQL **thực hiện trên bộ nhớ hay phải xuống đĩa.**
- Dựa vào 2 thông số:
  - **Innodb_buffer_pool_read_requests:** Tổng số yêu cầu gửi tới Buffer Pool trên bộ nhớ.
    ![Untitled](https://ngxquang.github.io/aws-ws1/images/2.optimization/009-buffer1.png)
  - **Innodb_buffer_pool_read:** Số yêu cầu phải xuống đĩa để lấy (Không tìm thấy trên Buffer Pool tại Memory)
    ![Untitled](https://ngxquang.github.io/aws-ws1/images/2.optimization/010-buffer2.png)
- Muốn **tính tỉ lệ buffer_cache_hit** theo công thức sau:
  ![Untitled](https://ngxquang.github.io/aws-ws1/images/2.optimization/014-formular.png)

- **Nếu tỷ lệ <90% thì cần tối ưu**

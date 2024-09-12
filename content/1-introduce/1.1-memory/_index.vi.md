---
title: "Kiến trúc trên memory"
date: "r Sys.Date()"
weight: 1
chapter: false
pre: " <b> 1.3 </b> "
---

- Khi cơ sở dữ liệu lưu trên memory, có **2 thành phần chính:**

  1. **Buffer pool (hoặc buffer cache):** Khi thực hiện 1 câu SELECT thì lấy dữ liệu từ buffer này.

     - Khi truy vấn lần đầu tiên, **dữ liệu được đọc từ đĩa lên và lưu vào buffer**, những lần đọc tiếp theo tương tự thì nó chỉ lấy dữ liệu từ buffer chứ không cần lấy từ đĩa.

  2. **Redo log (Vùng xử lý DML):** Lưu trữ những dữ liệu thay đổi của DML. Ví dụ trong buffer pool đang có giá trị là 10. Câu lệnh UPDATE thành 11 thì Redo log nó sẽ lưu Tại sao 10 → 11

![Minh họa kiến trúc trên memory](https://ngxquang.github.io/aws-ws1/images/1.introduce/001-memory.png)

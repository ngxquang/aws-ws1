---
title: "Kiến trúc phía ổ cứng"
date: "r Sys.Date()"
weight: 1
chapter: false
pre: " <b> 1.2 </b> "
---

- **Kiến trúc phía ổ cứng:** Chia thành nhiều thành phần (giống nhà chia thành nhiều phòng). Mỗi thành phần như vậy được gọi là **tablespace** (khái niệm logic)

  1. Các file có **cùng kiểu, có cùng loại tính chất với nhau** thì ghép vào cùng 1 tablespace
  2. Từ **buffer pool**, những dữ liệu thay đổi được **ghi xuống tablespace**. Hoặc buffer pool đọc dữ liệu từ các **datafile trong các tablespace**
  3. Có các loại tablespace:

     - **Hệ thống:** Khi cài đặt MySQL, các tablespace chứa các file hệ thống tự động được cài đặt trên system **(file ibdata1)**
     - **Undo Tablespace:** Nhiệm vụ thực hiện việc rollback cho các câu lệnh DML. Sự khác biệt giữa Redo log và Undo như sau:
       - **Redo log** cho biết quá trình diễn ra sự thay đổi dữ liệu đó. Trả lời cho câu hỏi: Tại sao 10 → 11. Nghĩa là khi giá trị thay đổi từ 10 → 11, redo log sẽ ghi lại cái thao tác đổi từ 10 → là update
       - **Undo** cho phép lấy giá trị trước đó. Trả lời cho câu hỏi: Bây giờ có giá trị 11, làm sao để quay về giá trị trước đây ?
     - **Temp Tablespace:** Thông thường khi code, ta sẽ tạo 1 bảng temp để thực hiện tính toán, sau đó xóa đi ⇒ Thiết kế này không ổn. Bản thân database đã có những vùng riêng cho temp. Khi kết thúc session thì tự động giải phóng.
     - **General tablespace**: Có thể tạo tablespace và tạo bảng trên tablespace đó. Ở những dự án lớn, có khái niệm là **quy hoạch vòng đời dữ liệu**. Ta có thể quy hoạch dữ liệu ở trên 1 table space cụ thể nào

     ![cmd1](https://ngxquang.github.io/aws-ws1/images/1.introduce/002-cmd1.png)

     ![cmd2](https://ngxquang.github.io/aws-ws1/images/1.introduce/003-cmd2.png)

     - **Các tablespace chứa dữ liệu, chứa các datafile**

  4. **Redo Log** cũng được ghi xuống Disk vào Redo Log File.
  5. **Doublewrite Buffer Files**
     - Khi dữ liệu được ghi vào đĩa, nó sẽ được ghi trước tiên vào doublewrite buffer.
     - Sau đó, từ doublewrite buffer, nó sẽ được ghi vào vị trí cuối cùng trong tablespace.
     - Nếu xảy ra sự cố trong quá trình ghi, InnoDB có thể sử dụng bản sao trong doublewrite buffer để khôi phục lại trang dữ liệu đó.
       ![harddisk](https://ngxquang.github.io/aws-ws1/images/1.introduce/004-arch.png)

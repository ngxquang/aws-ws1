---
title : "Partition"
date :  "r Sys.Date()" 
weight : 3
chapter : false
pre : " <b> 2.1.3 </b> "
---

1. Giả sử chúng ta tạo một bảng customers_partition, giống với bảng customers nhưng được phân chia thành các phân vùng (partition). Cấu trúc DDL của bảng này không khác biệt nhiều so với bảng thông thường, nhưng điểm nổi bật là cột Ngày giao dịch được dùng để tạo các phân vùng. Cụ thể, các giao dịch sẽ được chia vào từng partition dựa trên điều kiện LESS THAN year('Ngay_giao_dich'), mỗi partition giống như một tầng của tòa nhà dữ liệu.

2. Việc áp dụng partition giúp tăng tốc độ truy vấn, đặc biệt khi bảng dữ liệu có kích thước lớn. Tuy nhiên, để tận dụng tối đa hiệu quả của partition, điều kiện WHERE trong truy vấn cần phải bao gồm cột đã được sử dụng để tạo partition.

```
CREATE TABLE customers_partition (
  id INT,
  ten_khach_hang VARCHAR(100),
  ngay_giao_dich DATE
)
PARTITION BY RANGE (YEAR(ngay_giao_dich)) (
  PARTITION p0 VALUES LESS THAN (2015),
  PARTITION p1 VALUES LESS THAN (2020),
  PARTITION p2 VALUES LESS THAN (2025)
);
```

3. Giả sử như chúng ta có bảng customers_partition như trên

**PARTITION BY RANGE (YEAR(ngay_giao_dich)):**
Phân chia theo khoảng (RANGE Partitioning) dựa trên cột **ngay_giao_dich**. Ở đây, dữ liệu được phân vùng dựa trên năm của cột **ngay_giao_dich** bằng cách sử dụng hàm YEAR(), nghĩa là các giá trị **ngay_giao_dich** sẽ được chuyển thành năm để xác định phần dữ liệu thuộc partition nào.
Ví dụ: Nếu **ngay_giao_dich** là '2018-03-15', MySQL sẽ lấy năm '2018' để phân chia dữ liệu.


**PARTITION p0 VALUES LESS THAN (2015):** Partition p0 lưu trữ tất cả các hàng có giá trị của YEAR(ngay_giao_dich) nhỏ hơn năm 2015. Điều này có nghĩa là mọi giao dịch trước năm 2015 sẽ được lưu vào partition này.
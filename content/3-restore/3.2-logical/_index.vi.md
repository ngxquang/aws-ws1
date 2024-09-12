---
title : "Logical Restore"
date :  "r Sys.Date()" 
weight : 2 
chapter : false
pre : " <b> 3.2. </b> "
---

1. **Logical Backup** lưu trữ dữ liệu và cấu trúc của cơ sở dữ liệu dưới dạng câu lệnh SQL, ví dụ như **CREATE TABLE, INSERT INTO, v.v.** Cách này chủ yếu sao lưu nội dung của cơ sở dữ liệu (bao gồm bảng, dữ liệu, triggers, stored procedures, v.v.) mà không liên quan đến các tệp vật lý của cơ sở dữ liệu.

2. Công cụ phổ biến nhất để tạo Logical Backup trong MySQL là **mysqldump**.

3. Backup 1 bảng

   1. **Backup chỉ cấu trúc của bảng**
      - Câu lệnh:
      
      
mysqldump.exe -uroot -p <tên database> -d <tên bảng> > <đường dẫn folder>\<tên bảng>_ddl.sql

      
   2. **Backup chỉ dữ liệu bảng**
      - Câu lệnh:
      
      
mysqldump.exe -uroot -p <tên database> -t <tên bảng> > <đường dẫn folder>\<tên bảng>_data.sql

      
   3. **Backup cả cấu trúc và dữ liệu của bảng**
      - Câu lệnh:
      
      
mysqldump.exe -uroot -p <tên database> <tên bảng> > <đường dẫn folder>\<tên bảng>_table.sql

      

4. Backup 1 hoặc nhiều Database

   1. **Backup 1 database:**
      - Câu lệnh:
      
      
mysqldump.exe -uroot -p <tên database> > <đường dẫn folder>\<tên database>db.sql

      
   2. **Backup toàn bộ tất cả databases:**
      - Câu lệnh:
      
      
mysqldump.exe -uroot -p --all-database > <đường dẫn folder>\alldb.sql
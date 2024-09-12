---
title : "Physical Restore"
date :  "r Sys.Date()" 
weight : 1 
chapter : false
pre : " <b> 3.1. </b> "
---


1. **Physical Backup** trong MySQL là phương pháp **sao lưu toàn bộ các tệp vật lý của cơ sở dữ liệu**, bao gồm cả tệp dữ liệu, tệp log và tệp cấu hình, từ hệ thống lưu trữ

2. **Physical Backup** lưu trực tiếp các tệp hệ thống mà MySQL sử dụng để lưu trữ dữ liệu. Các tệp này bao gồm các tệp InnoDB data file, MyISAM data file, tệp log (log files), và các tệp cấu hình liên quan.

3. Dữ liệu được sao chép nguyên vẹn và được sử dụng lại ngay khi khôi phục, mà không cần phải thực thi lại các câu lệnh SQL như trong Logical Backup.
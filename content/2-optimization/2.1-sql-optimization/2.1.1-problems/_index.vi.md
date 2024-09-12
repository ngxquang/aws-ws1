---
title : "Vấn đề đặt ra"
date :  "r Sys.Date()" 
weight : 1 
chapter : false
pre : " <b> 2.1.1 </b> "
---

1. Giả sử có 1 câu lệnh SELECT, muốn tối ưu thì phải **xem chiến lược thực thi** của câu lệnh đó

![Untitled](/images/2.optimization/001-explain1.png)

2. Cách xem chiến lược thực thi: **Dùng EXPLAIN <câu lệnh>**

![Untitled](/images/2.optimization/002-explain2.png)

3. Các thông số quan trọng:
    - **table: customers:** Table mà nó đang quét
    - **type: ALL** (tương tự Full Table Scan): Quét hết toàn bộ bản ghi ở trong customers
    - **rows: 10:** Phán đoán của hệ thống có bao nhiêu bản ghi trong bảng. Có thể phán đoán sai
    - filtered: dự kiến sau khi quét 10 bản ghi của rows thì có bao nhiêu phần trăm là thỏa điều kiện where
    - Cần chú ý: Bất kỳ khi nào nhìn thấy type: ALL thì cần phải suy nghĩ lại. Nếu số lượng bản ghi nhỏ (10 - 100) thì không sao, nhưng số lượng hàng chục nghìn, hàng trăm nghìn thì rất tiêu tốn hiệu năng
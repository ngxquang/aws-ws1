---
title : "Table_cache_hit"
date :  "r Sys.Date()"
weight : 2
chapter : false
pre : " <b> 2.2.2 </b> "
---

- **Cache**: Nếu cache được trên bộ nhớ thì hiệu năng tăng.
- Bên trên thì cache trên mức block dữ liệu, còn ở phần này cache trên mức table
- Có 2 thông số để tính:
    - **Open_tables:** Tổng số table được open trong caches
    
    ![Untitled](/images/2.optimization/015-table1.png)
    
    - **Opened_tables:** Tổng số table được Open
    
    ![Untitled](/images/2.optimization/016-table2.png)
    
- Tính tỷ lệ **Table Cache Hit** theo công thức sau:
    ![Untitled](/images/2.optimization/018-formular2.png)


- **Nếu tỷ lệ < 80% thì cần tối ưu**
- **Tham số tối ưu: Tăng tham số table_open_cache**
    ![Untitled](/images/2.optimization/017-table3.png)
---
title : "Index"
date :  "r Sys.Date()" 
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---

1. **Tạo index trên 1 cột có trong điều kiện where:**
    
    ![Tạo index trên 1 cột](/images/2.optimization/003-index1.png)
    
    - Sự khác biệt khi EXPLAIN lại:
    
    ![Kết quả khi explain](/images/2.optimization/004-index2.png)
    
    - **type: ref:** type lúc này không phải ALL nữa mà là ref. Nghĩa là nó không quét toàn bộ bảng nữa mà nó quét index mình vừa tạo
        - **possible_keys: idx_namsinh:** Hệ thống có thể sử dụng những index nào để thực thi câu lệnh của mình
        - **key: idx_namsinh:** Trong đống possible_keys mà hệ thống thấy thì nó chọn duy nhất idx_namsinh
        - **rows: 1:** Giảm so với ở trên
2. **Tạo index trên nhiều cột (thường được áp dụng)**
    - Tạo index trên 2 cột:
    
    ![Tạo index trên nhiều cột](/images/2.optimization/005-index3.png)
    
    - Sự khác biệt khi EXPLAIN lại:
    
    ![Sau khi explain](/images/2.optimization/006-index4.png)
    
    - **possible_keys: idx_namsinh, idx_namsinh_ngaygd:** Hệ thống có thêm 1 index nữa là cái mình vừa tạo
        - key: idx_namsinh_ngaygd: Trong đống possible_keys mà hệ thống thấy thì nó chọn duy nhất idx_namsinh
        - rows: 1: Khi làm việc với csdl hàng nghìn dòng thì mới thấy được sự khác biệt. Ví dụ trên chỉ là demo
    - Lưu ý khi sử dụng **composite index (index trên nhiều cột):**
        - **Cột đầu tiên đóng vai trò cực kỳ quan trọng**
        - Giả sử ta chỉnh sửa câu lệnh trên thành chỉ có thuộc tính ngay_giao_dich thì sao?
        
        ![Ví dụ](/images/2.optimization/006-index4.png)
        
        - Cột Type: ALL: Nó lại phải quét hết dữ liệu bảng mặc dù mình đã tạo index ?
        - possible_keys: là NULL: ??? Tại sao mình đã đặt index trên 2 cột là cột nam_sinh và ngay_giao_dich nhưng không có ???
        - ⇒ Cột đầu tiên rất quan trọng trong composite index. Nếu tạo 1 composite index khác mà đưa ngay_giao_dich lên trước thì nó sẽ khác:
        
        ![Sau khi explain](/images/2.optimization/007-index5.png)
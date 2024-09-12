---
title: "Index"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2.1.2 </b> "
---

1. **Creating an index on a column used in the WHERE condition:**

   ![Creating index on a column](https://ngxquang.github.io/aws-ws1/images/2.optimization/003-index1.png)

   - The difference when running EXPLAIN again:

   ![Result after explain](https://ngxquang.github.io/aws-ws1/images/2.optimization/004-index2.png)

   - **type: ref:** The type is no longer ALL but ref. This means it does not scan the entire table but rather scans the index that was just created.
     - **possible_keys: idx_namsinh:** The system lists the possible indexes it could use to execute the statement.
     - **key: idx_namsinh:** Among the possible_keys, the system selects only idx_namsinh.
     - **rows: 1:** Reduced compared to before.

2. **Creating an index on multiple columns (commonly applied):**

   - Creating an index on 2 columns:

   ![Creating index on multiple columns](https://ngxquang.github.io/aws-ws1/images/2.optimization/005-index3.png)

   - The difference when running EXPLAIN again:

   ![After explain](https://ngxquang.github.io/aws-ws1/images/2.optimization/006-index4.png)

   - **possible_keys: idx_namsinh, idx_namsinh_ngaygd:** The system now includes an additional index, which is the one just created.
     - key: idx_namsinh_ngaygd: Among the possible_keys, the system selects only idx_namsinh.
     - rows: 1: The difference becomes apparent when working with thousands of rows in a database. The example above is just a demo.
   - Notes when using **composite index (index on multiple columns):**
     - **The first column plays a crucial role.**
     - Suppose you modify the statement to include only the ngay_giao_dich attribute, what happens?
       ![Example](https://ngxquang.github.io/aws-ws1/images/2.optimization/006-index4.png)
     - Column Type: ALL: It has to scan the entire table even though an index was created?
     - possible_keys: NULL: ??? Why is there no index on the columns nam_sinh and ngay_giao_dich even though they were indexed???
     - ⇒ The first column is very important in a composite index. If you create another composite index with ngay_giao_dich first, it will be different:
       ![After explain](https://ngxquang.github.io/aws-ws1/images/2.optimization/007-index5.png)

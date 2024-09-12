---
title: "Partition"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 2.1.3 </b> "
---

1. Suppose we create a table `customers_partition`, similar to the `customers` table but divided into partitions. The DDL structure of this table is not significantly different from a regular table, but the key feature is that the transaction date column is used to create the partitions. Specifically, transactions are divided into partitions based on the condition LESS THAN year('Ngay_giao_dich'), with each partition resembling a floor of the data building.

2. Applying partitioning helps speed up queries, especially when dealing with large tables. However, to fully utilize the benefits of partitioning, the WHERE condition in the query must include the column used to create the partitions.

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

3. Suppose we have the `customers_partition` table as above:

**PARTITION BY RANGE (YEAR(ngay_giao_dich)):**
Partitions by range (RANGE Partitioning) based on the **ngay_giao_dich** column. Here, the data is partitioned based on the year of the **ngay_giao_dich** column using the YEAR() function, meaning the **ngay_giao_dich** values are converted to the year to determine which partition the data belongs to.
For example: If **ngay_giao_dich** is '2018-03-15', MySQL will use the year '2018' to partition the data.

**PARTITION p0 VALUES LESS THAN (2015):** Partition p0 stores all rows with YEAR(ngay_giao_dich) values less than the year 2015. This means all transactions before 2015 will be stored in this partition.


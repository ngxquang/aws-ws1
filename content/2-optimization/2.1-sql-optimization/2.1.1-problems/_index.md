---
title: "The Problem Statement"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 2.1.1 </b> "
---

1. Suppose there is a SELECT statement, to optimize it you need to **review the execution plan** of the statement.

![Untitled](/images/2.optimization/001-explain1.png)

2. How to view the execution plan: **Use EXPLAIN <statement>**

![Untitled](/images/2.optimization/002-explain2.png)

3. Important parameters:
    - **table: customers:** The table being scanned.
    - **type: ALL** (similar to Full Table Scan): Scans all records in the customers table.
    - **rows: 10:** The system's estimate of how many records are in the table. This estimate may be incorrect.
    - filtered: The expected percentage of rows satisfying the WHERE condition after scanning 10 rows.
    - Note: Whenever you see type: ALL, it needs to be reconsidered. If the number of records is small (10 - 100), it is not a problem, but with tens of thousands or hundreds of thousands of rows, it can be very performance-intensive.

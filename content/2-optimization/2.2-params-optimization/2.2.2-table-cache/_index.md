---
title: "Table_cache_hit"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 2.2.2 </b> "
---

- **Cache:** When data is cached in memory, performance improves.
- While the previous section covered block-level caching, this section deals with table-level caching.
- There are two metrics for calculation:
    - **Open_tables:** Total number of tables open in the cache.
    
    ![Untitled](/images/2.optimization/015-table1.png)
    
    - **Opened_tables:** Total number of tables opened.
    
    ![Untitled](/images/2.optimization/016-table2.png)
    
- Calculate the **Table Cache Hit** ratio using the following formula:
    ![Untitled](/images/2.optimization/018-formular2.png)

- **If the ratio is < 80%, optimization is needed.**
- **Optimization Parameter: Increase the table_open_cache parameter.**
    ![Untitled](/images/2.optimization/017-table3.png)

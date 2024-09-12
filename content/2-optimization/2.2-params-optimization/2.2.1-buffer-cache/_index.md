---
title: "Buffer_cache_hit"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 2.2.1 </b> "
---

- The **buffer_cache_hit** ratio indicates the memory usage of MySQL.
- This ratio reflects whether MySQL **performs operations in memory or needs to go to disk**.
- Based on two metrics:
    - **Innodb_buffer_pool_read_requests:** Total number of requests sent to the Buffer Pool in memory.
    
    ![Untitled](/images/2.optimization/009-buffer1.png)
    
    - **Innodb_buffer_pool_read:** Number of requests that had to go to disk to retrieve data (not found in the Buffer Pool in memory).
    
    ![Untitled](/images/2.optimization/010-buffer2.png)
    
- To **calculate the buffer_cache_hit ratio**, use the following formula:
    ![Untitled](/images/2.optimization/014-formular.png)

- **If the ratio is <90%, optimization is needed.**

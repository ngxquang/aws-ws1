---
title: "Memory Architecture"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.3 </b> "
---
- When the database is stored in memory, there are **2 main components:**
    1. **Buffer pool (or buffer cache):** When executing a SELECT statement, data is retrieved from this buffer.
        - During the first query, **data is read from disk and stored in the buffer**, and subsequent reads of the same data will fetch it from the buffer rather than from the disk.
    
    2. **Redo log (DML processing area):** Stores the changes made by DML. For example, if the buffer pool holds a value of 10, and an UPDATE statement changes it to 11, the Redo log will record why 10 → 11.

![Illustration of memory architecture](https://ngxquang.github.io/aws-ws1/images/1.introduce/001-memory.png)

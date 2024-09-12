---
title: "Hard Disk Architecture"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.2 </b> "
---

- **Hard Disk Architecture:** Divided into several components (similar to how a house is divided into rooms). Each such component is called a **tablespace** (logical concept).

  1. Files with **the same type and characteristics** are grouped into the same tablespace.
  2. From the **buffer pool**, changed data is **written to the tablespace**. Alternatively, the buffer pool reads data from **datafiles within tablespaces**.
  3. There are several types of tablespaces:

     - **System:** When MySQL is installed, the tablespaces containing system files are automatically installed on the system **(file ibdata1)**.
     - **Undo Tablespace:** Responsible for performing rollback operations for DML statements. The difference between Redo log and Undo is as follows:
       - **Redo log** shows the process of data changes. It answers the question: Why 10 → 11. Meaning, when the value changes from 10 → 11, the redo log will record the action of changing from 10 → as update.
       - **Undo** allows retrieving the previous value. It answers the question: Now we have a value of 11, how can we revert to the previous value?
     - **Temp Tablespace:** Typically, when coding, a temporary table is created for calculations and then deleted ⇒ This design is not ideal. The database itself has dedicated areas for temp. It is automatically freed at the end of the session.
     - **General tablespace:** Tablespaces can be created and tables can be created within that tablespace. In large projects, there is the concept of **data lifecycle management**. We can manage data in a specific tablespace.

   ![cmd1](https://ngxquang.github.io/aws-ws1/images/1.introduce/002-cmd1.png)

   ![cmd2](https://ngxquang.github.io/aws-ws1/images/1.introduce/003-cmd2.png)

     - **Tablespaces contain data and datafiles**

  4. **Redo Log** is also written to Disk into the Redo Log File.
  5. **Doublewrite Buffer Files**
     - When data is written to disk, it is first written to the doublewrite buffer.
     - Then, from the doublewrite buffer, it is written to its final location in the tablespace.
     - If a failure occurs during the write process, InnoDB can use the copy in the doublewrite buffer to recover the data page.
      ![harddisk](https://ngxquang.github.io/aws-ws1/images/1.introduce/004-arch.png)
